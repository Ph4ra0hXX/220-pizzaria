<script setup>
import { ref } from "vue";

const props = defineProps({
  totalPrice: {
    type: Number,
    required: true,
  },
  cartItems: {
    type: Array,
    required: true,
  },
});

const emit = defineEmits(["complete-order", "back-to-cart"]);

const currentStep = ref("delivery");
const deliveryType = ref("delivery"); // 'delivery' ou 'pickup'
const paymentMethod = ref("pix");
const pixKey = "88994812041";
const copyingPix = ref(false);

const copyPix = async () => {
  try {
    await navigator.clipboard.writeText(pixKey);
    copyingPix.value = true;
    setTimeout(() => (copyingPix.value = false), 1500);
  } catch (err) {
    const textarea = document.createElement("textarea");
    textarea.value = pixKey;
    textarea.style.position = "fixed";
    textarea.style.left = "-9999px";
    document.body.appendChild(textarea);
    textarea.select();
    try {
      document.execCommand("copy");
      copyingPix.value = true;
      setTimeout(() => (copyingPix.value = false), 1500);
    } finally {
      document.body.removeChild(textarea);
    }
  }
};

// Informações de retirada
const deliveryInfo = ref({
  name: "",
  street: "",
  number: "",
  complement: "",
  neighborhood: "",
});

// Erros de validação
const errors = ref({
  name: "",
  street: "",
  number: "",
  neighborhood: "",
});

const goToPayment = () => {
  if (validateDeliveryInfo()) {
    currentStep.value = "payment";
  }
};

const goBackToDelivery = () => {
  currentStep.value = "delivery";
};

const validateDeliveryInfo = () => {
  const info = deliveryInfo.value;
  let isValid = true;

  // Limpar erros anteriores
  errors.value = {
    name: "",
    street: "",
    number: "",
    neighborhood: "",
  };

  if (!String(info.name ?? "").trim()) {
    errors.value.name = "Por favor, informe seu nome";
    isValid = false;
  }

  // Se for entrega, validar endereço completo
  if (deliveryType.value === "delivery") {
    if (!String(info.street ?? "").trim()) {
      errors.value.street = "Por favor, informe a rua";
      isValid = false;
    }
    if (!String(info.number ?? "").trim()) {
      errors.value.number = "Por favor, informe o número da casa";
      isValid = false;
    }
    if (!String(info.neighborhood ?? "").trim()) {
      errors.value.neighborhood = "Por favor, informe o bairro";
      isValid = false;
    }
  }

  return isValid;
};

const validatePaymentInfo = () => {
  return true;
};

const formatOrderForWhatsApp = () => {
  let message = "";

  message += "*CLIENTE:*\n";
  message += `Nome: ${deliveryInfo.value.name}\n`;

  if (deliveryType.value === "delivery") {
    message += `Rua: ${deliveryInfo.value.street}\n`;
    message += `Número: ${deliveryInfo.value.number}\n`;
    if (deliveryInfo.value.complement) {
      message += `Complemento: ${deliveryInfo.value.complement}\n`;
    }
    message += `Bairro: ${deliveryInfo.value.neighborhood}\n`;
  } else {
    message += `Tipo: IR BUSCAR (SEM TAXA)\n`;
  }
  message += "\n";

  message += "*ITENS DO PEDIDO:*\n";

  // Separar pizzas e bebidas
  const pizzaItems = [];
  const drinkItems = [];

  props.cartItems.forEach((item) => {
    // Se for uma bebida (verifica pela categoria ou pelo objeto drink)
    if (item.drink || (item.pizza && item.pizza.category === "BEBIDA")) {
      drinkItems.push(item);
      return;
    }
    pizzaItems.push(item);
  });

  // Processa pizzas
  pizzaItems.forEach((item) => {
    const itemSize = item.size ? ` (${item.size})` : "";
    const itemPrice = item.price.toFixed(2);
    // Pizza G com 1 flavor adicional = 2 metades (principal + flavor)
    const hasTwoFlavors =
      item.flavors && item.flavors.length === 1 && item.size === "G";
    const sumNote = hasTwoFlavors ? "" : "";

    // Mostra "PIZZA" seguido do tamanho e preço
    message += `- PIZZA${itemSize} - R$ ${itemPrice}${sumNote}\n`;

    // Se tem sabores adicionais (flavors), adiciona a pizza principal como 1/2
    if (item.flavors && item.flavors.length > 0) {
      if (item.size === "G" && item.flavors.length === 1) {
        // Pizza G com 1 flavor adicional = 2 metades
        const mainHalfPrice = (item.pizza.prices[item.size] / 2).toFixed(2);
        message += `  + 1/2 ${item.pizza.name} ${mainHalfPrice}\n`;
        item.flavors.forEach((flavor) => {
          const flavorHalfPrice = (flavor.prices[item.size] / 2).toFixed(2);
          message += `  + 1/2 ${flavor.name} ${flavorHalfPrice}\n`;
        });
      } else if (item.size === "P") {
        message += `  + 1 ${item.pizza.name}\n`;
        item.flavors.forEach((flavor) => {
          message += `  + 1 ${flavor.name}\n`;
        });
      } else {
        message += `  + Com: ${item.flavors.map((f) => f.name).join(", ")}\n`;
      }
    } else {
      // Se NÃO tem sabores adicionais, adiciona a pizza principal como 1
      message += `  + 1 ${item.pizza.name}\n`;
    }

    if (item.edge) {
      message += `  + Borda: ${item.edge.name} (+R$ ${item.edge.price.toFixed(2)})\n`;
    }
    if (item.additionals && item.additionals.length > 0) {
      message += `  + Adicionais:\n`;
      item.additionals.forEach((additional) => {
        message += `    - ${additional.name} (+R$ ${additional.price.toFixed(2)})\n`;
      });
    }
    if (item.comment) {
      message += `  + Obs: ${item.comment}\n`;
    }
  });

  // Processa bebidas separadamente
  if (drinkItems.length > 0) {
    message += `* Bebidas *\n`;
    drinkItems.forEach((item) => {
      // Verifica se a bebida está em item.drink ou item.pizza
      const drinkName = item.drink ? item.drink.name : item.pizza.name;
      const drinkPrice = item.drink ? item.drink.price : item.price;
      message += `  + 1 ${drinkName} - R$ ${drinkPrice.toFixed(2)}\n`;
    });
  }

  const deliveryFee = deliveryType.value === "delivery" ? 5 : 0;
  if (deliveryType.value === "delivery") {
    message += `\n*TAXA DE ENTREGA:* R$ 5.00\n`;
  } else {
    message += `\n*TAXA DE ENTREGA:* GRÁTIS (IR BUSCAR)\n`;
  }
  message += `*TOTAL: R$ ${(props.totalPrice + deliveryFee).toFixed(2)}*\n`;
  message += `*METODO DE PAGAMENTO:* ${getPaymentMethodName(paymentMethod.value)}\n`;

  // Adiciona data e hora do pedido
  const now = new Date();
  message += `\n${now.toLocaleDateString("pt-BR")} às ${now.toLocaleTimeString("pt-BR", { hour: "2-digit", minute: "2-digit" })}`;

  return message;
};

const getPaymentMethodName = (method) => {
  const methods = {
    pix: "PIX",
    credit: "Cartão de Crédito",
    debit: "Cartão de Débito",
    cash: "Dinheiro",
  };
  return methods[method] || method;
};

const sendToWhatsApp = () => {
  const whatsappNumber = "558896954495";
  const message = formatOrderForWhatsApp();
  const encodedMessage = encodeURIComponent(message);
  const whatsappUrl = `https://wa.me/${whatsappNumber}?text=${encodedMessage}`;

  window.open(whatsappUrl, "_blank");
};

const completeOrder = () => {
  const deliveryFee = deliveryType.value === "delivery" ? 5 : 0;
  const order = {
    deliveryInfo: deliveryInfo.value,
    deliveryType: deliveryType.value,
    paymentMethod: paymentMethod.value,
    items: props.cartItems,
    total: props.totalPrice + deliveryFee,
    timestamp: new Date(),
  };

  sendToWhatsApp();
  emit("complete-order", order);
};

const getTotalWithDelivery = () => {
  return deliveryType.value === "delivery"
    ? props.totalPrice + 5
    : props.totalPrice;
};
</script>

<template>
  <div class="checkout-container">
    <div class="checkout-header">
      <h2>Finalizar Pedido</h2>
      <div class="steps-indicator">
        <div :class="['step', { active: currentStep === 'delivery' }]">
          <span class="step-number">1</span>
          <span class="step-label">Retirada</span>
        </div>
        <div class="step-connector"></div>
        <div :class="['step', { active: currentStep === 'payment' }]">
          <span class="step-number">2</span>
          <span class="step-label">Pagamento</span>
        </div>
      </div>
    </div>

    <!-- Formulário de Retirada -->
    <div v-if="currentStep === 'delivery'" class="form-section">
      <h3>Informações de Retirada</h3>

      <!-- Seletor de Tipo de Entrega -->
      <div class="delivery-type-selector">
        <label class="delivery-type-option">
          <input type="radio" v-model="deliveryType" value="delivery" />
          <span class="type-icon">🏍️</span>
          <span class="type-info">
            <span class="type-name">Entrega</span>
            <span class="type-price">R$ 5,00</span>
          </span>
        </label>

        <label class="delivery-type-option">
          <input type="radio" v-model="deliveryType" value="pickup" />
          <span class="type-icon">🏪</span>
          <span class="type-info">
            <span class="type-name">Ir Buscar</span>
            <span class="type-price">Grátis</span>
          </span>
        </label>
      </div>

      <div class="form-group">
        <label for="name">Nome Completo *</label>
        <input
          id="name"
          v-model="deliveryInfo.name"
          type="text"
          placeholder="Seu nome completo"
          :class="{ 'input-error': errors.name }"
        />
        <span v-if="errors.name" class="error-message">{{ errors.name }}</span>
      </div>

      <div v-if="deliveryType === 'delivery'" class="address-section">
        <h4>Endereço para Entrega</h4>

        <div class="form-group">
          <label for="street">Rua *</label>
          <input
            id="street"
            v-model="deliveryInfo.street"
            type="text"
            placeholder="Nome da rua"
            :class="{ 'input-error': errors.street }"
          />
          <span v-if="errors.street" class="error-message">{{
            errors.street
          }}</span>
        </div>

        <div class="form-row">
          <div class="form-group">
            <label for="number">Número *</label>
            <input
              id="number"
              v-model="deliveryInfo.number"
              type="number"
              placeholder="000"
              :class="{ 'input-error': errors.number }"
            />
            <span v-if="errors.number" class="error-message">{{
              errors.number
            }}</span>
          </div>

          <div class="form-group">
            <label for="neighborhood">Bairro *</label>
            <input
              id="neighborhood"
              v-model="deliveryInfo.neighborhood"
              type="text"
              placeholder="Nome do bairro"
              :class="{ 'input-error': errors.neighborhood }"
            />
            <span v-if="errors.neighborhood" class="error-message">{{
              errors.neighborhood
            }}</span>
          </div>
        </div>

        <div class="form-group">
          <label for="complement">Complemento</label>
          <input
            id="complement"
            v-model="deliveryInfo.complement"
            type="text"
            placeholder="Apto, bloco, etc"
          />
        </div>
      </div>

      <div class="form-actions">
        <button @click="$emit('back-to-cart')" class="btn-secondary">
          Voltar ao Carrinho
        </button>
        <button @click="goToPayment" class="btn-primary">
          Prosseguir para Pagamento →
        </button>
      </div>
    </div>

    <!-- Formulário de Pagamento -->
    <div v-if="currentStep === 'payment'" class="form-section">
      <h3>Método de Pagamento</h3>

      <div class="payment-methods">
        <label class="payment-option">
          <input type="radio" v-model="paymentMethod" value="pix" />
          <span class="method-icon">💳</span>
          <span class="method-name">PIX</span>
        </label>

        <label class="payment-option">
          <input type="radio" v-model="paymentMethod" value="credit" />
          <span class="method-icon">💳</span>
          <span class="method-name">Cartão de Crédito</span>
        </label>

        <label class="payment-option">
          <input type="radio" v-model="paymentMethod" value="debit" />
          <span class="method-icon">🏦</span>
          <span class="method-name">Cartão de Débito</span>
        </label>

        <label class="payment-option">
          <input type="radio" v-model="paymentMethod" value="cash" />
          <span class="method-icon">💵</span>
          <span class="method-name">Dinheiro</span>
        </label>
      </div>

      <div v-if="paymentMethod === 'pix'" class="pix-section">
        <div class="pix-info">
          <div class="pix-line">
            <span>Chave PIX:</span>
            <strong>{{ pixKey }}</strong>
          </div>
          <div class="pix-beneficiary">
            <p><strong>Beneficiário:</strong> Herbene Carneiro Girão</p>
            <p><strong>Banco:</strong> Banco Inter</p>
          </div>
        </div>
        <button @click="copyPix" class="btn-secondary pix-copy-btn">
          {{ copyingPix ? "Copiado!" : "Copiar PIX" }}
        </button>
      </div>

      <div class="payment-summary">
        <div class="summary-line">
          <span>Subtotal:</span>
          <span>R$ {{ totalPrice.toFixed(2) }}</span>
        </div>
        <div v-if="deliveryType === 'delivery'" class="summary-line">
          <span>Taxa de entrega:</span>
          <span>R$ 5,00</span>
        </div>
        <div v-else class="summary-line delivery-free">
          <span>Taxa de entrega:</span>
          <span>GRÁTIS (Ir Buscar)</span>
        </div>
        <div class="summary-line total">
          <span>Total a pagar:</span>
          <span>R$ {{ getTotalWithDelivery().toFixed(2) }}</span>
        </div>
      </div>

      <div class="form-actions">
        <button @click="goBackToDelivery" class="btn-secondary">
          ← Voltar
        </button>
        <button @click="completeOrder" class="btn-primary btn-complete">
          Confirmar Pedido
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.checkout-container {
  background: white;
  border-radius: 12px;
  padding: 2rem;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
}

.checkout-header {
  margin-bottom: 2rem;
  border-bottom: 2px solid #f0f0f0;
  padding-bottom: 1.5rem;
}

.checkout-header h2 {
  color: #000;
  margin-bottom: 1.5rem;
  font-size: 1.5rem;
}

.steps-indicator {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 1rem;
}

.step {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  opacity: 0.5;
  transition: opacity 0.3s;
}

.step.active {
  opacity: 1;
}

.step-number {
  width: 40px;
  height: 40px;
  background: #f0f0f0;
  border: 2px solid #ddd;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
  color: #666;
  transition: all 0.3s;
}

.step.active .step-number {
  background: #c61818;
  color: white;
  border-color: #c61818;
}

.step-label {
  font-size: 0.85rem;
  font-weight: 600;
  color: #666;
}

.step.active .step-label {
  color: #c61818;
}

.step-connector {
  width: 60px;
  height: 2px;
  background: #ddd;
  margin: 0 0.5rem;
}

.form-section {
  animation: slideIn 0.3s ease-out;
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.form-section h3 {
  color: #000;
  font-size: 1.3rem;
  margin-bottom: 1.5rem;
  color: #c61818;
}

.form-section h4 {
  color: #333;
  font-size: 1.1rem;
  margin: 1.5rem 0 1rem 0;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid #f0f0f0;
}

.form-group {
  margin-bottom: 1.2rem;
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-group label {
  font-weight: 600;
  color: #333;
  font-size: 0.95rem;
}

.form-group input,
.form-group select {
  padding: 0.75rem;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-size: 0.95rem;
  font-family: inherit;
  transition: all 0.3s;
  background: #f9f9f9;
}

.form-group input:focus,
.form-group select:focus {
  outline: none;
  border-color: #c61818;
  background: white;
  box-shadow: 0 0 0 3px rgba(198, 24, 24, 0.1);
}

.input-error {
  border-color: #dc3545 !important;
  background-color: #fff5f5 !important;
}

.error-message {
  color: #dc3545;
  font-size: 0.85rem;
  margin-top: 0.4rem;
  display: block;
  font-weight: 500;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
}

.delivery-type-selector {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  margin-bottom: 2rem;
}

.delivery-type-option {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1.2rem;
  border: 2px solid #ddd;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s;
  background: #f9f9f9;
}

.delivery-type-option:hover {
  border-color: #c61818;
  background: #fff;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.delivery-type-option input[type="radio"] {
  cursor: pointer;
  width: 20px;
  height: 20px;
  accent-color: #c61818;
}

.delivery-type-option input[type="radio"]:checked {
  transform: scale(1.1);
}

.delivery-type-option:has(input[type="radio"]:checked) {
  border-color: #c61818;
  background: #fff;
  box-shadow: 0 4px 12px rgba(198, 24, 24, 0.2);
}

.type-icon {
  font-size: 2rem;
}

.type-info {
  display: flex;
  flex-direction: column;
  flex: 1;
}

.type-name {
  font-weight: 700;
  color: #333;
  font-size: 1.1rem;
}

.type-price {
  color: #666;
  font-size: 0.9rem;
  margin-top: 0.2rem;
}

.delivery-type-option:has(input[type="radio"]:checked) .type-name {
  color: #c61818;
}

.delivery-type-option:has(input[type="radio"]:checked) .type-price {
  color: #c61818;
  font-weight: 600;
}

.address-section {
  background: #f9f9f9;
  padding: 1.5rem;
  border-radius: 8px;
  margin-bottom: 1rem;
  border-left: 4px solid #c61818;
}

.payment-methods {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  margin-bottom: 2rem;
}

.payment-option {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1.2rem;
  border: 2px solid #ddd;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s;
  background: #f9f9f9;
}

.payment-option input[type="radio"] {
  cursor: pointer;
  width: 20px;
  height: 20px;
  accent-color: #c61818;
}

.payment-option:hover {
  border-color: #c61818;
  background: #fff;
}

.payment-option input[type="radio"]:checked + .method-icon {
  color: #c61818;
}

.payment-option input[type="radio"]:checked ~ .method-name {
  color: #c61818;
  font-weight: 700;
}

.method-icon {
  font-size: 1.8rem;
  transition: all 0.3s;
}

.method-name {
  font-weight: 600;
  color: #333;
  transition: all 0.3s;
}

.payment-summary {
  background: #ffecec;
  padding: 1.5rem;
  border-radius: 8px;
  margin-bottom: 1.5rem;
  border-top: 2px solid #c61818;
}

.pix-section {
  background: #f9f9f9;
  padding: 1rem;
  border-radius: 8px;
  border: 2px dashed #c61818;
  margin-bottom: 1.5rem;
}

.pix-info {
  margin-bottom: 1rem;
}

.pix-line {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid #ddd;
}

.pix-beneficiary {
  background: white;
  padding: 1rem;
  border-radius: 6px;
  border-left: 3px solid #c61818;
}

.pix-beneficiary p {
  margin: 0.5rem 0;
  color: #333;
  font-size: 0.95rem;
}

.pix-beneficiary strong {
  color: #c61818;
}

.pix-copy-btn {
  text-transform: none;
}

.summary-line {
  display: flex;
  justify-content: space-between;
  padding: 0.8rem 0;
  color: #333;
  font-size: 1rem;
}

.summary-line.delivery-free {
  color: #28a745;
  font-weight: 600;
}

.summary-line.total {
  border-top: 2px solid #c61818;
  padding-top: 1rem;
  font-size: 1.2rem;
  font-weight: 700;
  color: #000;
}

.form-actions {
  display: flex;
  gap: 1rem;
  margin-top: 2rem;
}

.btn-primary,
.btn-secondary {
  flex: 1;
  padding: 1rem;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.btn-primary {
  background: #e8383f;
  color: white;
  box-shadow: 0 4px 15px rgba(198, 24, 24, 0.3);
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(198, 24, 24, 0.4);
}

.btn-primary:active {
  transform: translateY(0);
}

.btn-secondary {
  background: white;
  color: #c61818;
  border: 2px solid #c61818;
}

.btn-secondary:hover {
  background: #f9f9f9;
}

@media (max-width: 768px) {
  .checkout-container {
    padding: 1.5rem;
  }

  .delivery-type-selector {
    grid-template-columns: 1fr;
  }

  .form-row {
    grid-template-columns: 1fr;
  }

  .payment-methods {
    grid-template-columns: 1fr;
  }

  .form-actions {
    flex-direction: column;
  }

  .steps-indicator {
    flex-wrap: wrap;
  }
}
</style>
