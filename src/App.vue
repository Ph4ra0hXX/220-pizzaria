<script setup>
import { ref } from "vue";
import PizzaList from "./components/PizzaList.vue";
import PizzaDetail from "./components/PizzaDetail.vue";
import CheckoutForm from "./components/CheckoutForm.vue";

const pizzas = ref([
  {
    id: 1,
    name: "PIZZA MARGUERITA",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "TOMATE",
      "MANJERICÃO",
      "AZEITE DE OLIVA",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 38.0, G: 46.0 },
  },
  {
    id: 2,
    name: "PIZZA DE MUSSARELA",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { P: 37.0, G: 48.0 },
  },
  {
    id: 3,
    name: "PIZZA DE CALABRESA",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "CALABRESA FATIADA",
      "CEBOLA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { P: 37.0, G: 48.0 },
  },
  {
    id: 4,
    name: "PIZZA DE CALABRESA COM CATUPIRY",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "CALABRESA FATIADA",
      "CATUPIRY",
      "CEBOLA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { P: 42.0, G: 58.0 },
  },
  {
    id: 5,
    name: "PIZZA DE PORTUGUESA",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "PRESUNTO",
      "OVOS",
      "CEBOLA",
      "MILHO VERDE",
      "PIMENTAO",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { P: 37.0, G: 48.0 },
  },
  {
    id: 6,
    name: "PIZZA DE FRANGO",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "FRANGO",
      "MILHO VERDE",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { P: 37.0, G: 48.0 },
  },
  {
    id: 7,
    name: "PIZZA DE FRANGO COM CATUPIRY",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "FRANGO",
      "CATUPIRY",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { P: 42.0, G: 56.0 },
  },
  {
    id: 8,
    name: "PIZZA BACON",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "BACON",
      "CEBOLA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { P: 37.0, G: 54.0 },
  },
  {
    id: 9,
    name: "MISTA",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "PRESUNTO",
      "AZEITONA",
      "OREGANO",
      "CEBOLA",
    ],
    prices: { P: 37.0, G: 48.0 },
  },
  {
    id: 10,
    name: "PIZZA DE CAMARÃO",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "CAMARÃO REFOGADO",
      "TOMATE CEREJA",
      "ALHO TORRADO",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { P: 44.0, G: 66.0 },
  },
  {
    id: 11,
    name: "PIZZA DE LOMBO",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "LOMBINHO",
      "CEBOLA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { P: 39.0, G: 53.0 },
  },
  {
    id: 12,
    name: "PIZZA DE LOMBO COM ABACAXI",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "LOMBINHO",
      "ABACAXI CARAMELIZADO",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { P: 42.0, G: 56.0 },
  },
  {
    id: 13,
    name: "PIZZA DE CARNE DE SOL",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "CARNE DO SOL",
      "CEBOLA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { P: 42.0, G: 56.0 },
  },
  {
    id: 14,
    name: "PIZZA DE CARNE DE SOL COM CATUPIRY",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "CARNE DO SOL",
      "CATUPIRY",
      "CEBOLA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { P: 44.0, G: 66.0 },
  },
  {
    id: 14,
    name: "DISQUETE",
    category: "DOCE",
    ingredients: ["CHOCOLATE AO LEITE", "DISQUETES"],
    prices: { P: 39.0, G: 52.0 },
  },
  {
    id: 15,
    name: "BIS",
    category: "DOCE",
    ingredients: ["CHOCOLATE AO LEITE", "BIS PICADO"],
    prices: { P: 39.0, G: 52.0 },
  },
  {
    id: 16,
    name: "OURO BRANCO",
    category: "DOCE",
    ingredients: [
      "CHOCOLATE BRANCO",
      "BOMBONS OURO BRANCO",
      "CHOCOLATE AO LEITE",
    ],
    prices: { P: 45.0, G: 66.0 },
  },
  {
    id: 17,
    name: "COCA COLA 1L",
    category: "BEBIDA",
    ingredients: [],
    prices: { unit: 11.0 },
  },
  {
    id: 18,
    name: "COCA ZERO 1L",
    category: "BEBIDA",
    ingredients: [],
    prices: { unit: 11.0 },
  },
  {
    id: 19,
    name: "GUARANA ANTARTICA 1L",
    category: "BEBIDA",
    ingredients: [],
    prices: { unit: 11.0 },
  },
  {
    id: 20,
    name: "FRANBACON",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "FRANGO",
      "BACON",
      "MILHO VERDE",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 39.0, G: 52.0 },
  },
  {
    id: 21,
    name: "FRANBACON COM CATUPIRY",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "FRANGO",
      "BACON",
      "CATUPIRY",
      "MILHO VERDE",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 44.0, G: 58.0 },
  },
  {
    id: 22,
    name: "PORTUGUESA DA CASA",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "PRESUNTO",
      "CALABRESA",
      "OVO",
      "CEBOLA",
      "PIMENTAO",
      "GELEIA DE PIMENTA",
      "MILHO VERDE",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 39.0, G: 52.0 },
  },
  {
    id: 23,
    name: "BACONDA CASA",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "BACON",
      "TOMATE CEREJA",
      "GELEIA DE PIMENTA",
      "MANJERICÃO",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 42.0, G: 56.0 },
  },
  {
    id: 24,
    name: "LOMBINHO COM CATUPIRY",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "LOMBINHO",
      "CATUPIRY",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 42.0, G: 56.0 },
  },
  {
    id: 25,
    name: "CARNE DE SOL DA CASA",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "CARNE DE SOL",
      "QUEIJO COALHO",
      "CEBOLA",
      "PIMENTAO",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 44.0, G: 66.0 },
  },
  {
    id: 27,
    name: "CAMARÃO SUPREME",
    category: "ESPECIAL",
    ingredients: [
      "MASSA 25cm",
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "CAMARÃO",
      "TOMATE CEREJA",
      "GENGIBRE",
      "MANJERICÃO",
      "MOLHO TARÊ",
      "OREGANO",
      "AZEITONA",
    ],
    prices: { P: 52.0, G: 72.0 },
  },
  // {
  //   id: 28,
  //   name: "PIZZA DE CALABRESA + Guaraná Antártica 1L",
  //   category: "PROMOÇÃO",
  //   ingredients: [
  //     "MOLHO DE TOMATE ESPECIAL",
  //     "MUSSARELA",
  //     "CALABRESA FATIADA",
  //     "CEBOLA",
  //     "AZEITONAS",
  //     "OREGANO",
  //   ],
  //   prices: { G: 43.0 },
  // },
  // {
  //   id: 29,
  //   name: "MISTA + Guaraná Antártica 1L",
  //   category: "PROMOÇÃO",
  //   ingredients: [
  //     "MOLHO DE TOMATE",
  //     "MUSSARELA",
  //     "PRESUNTO",
  //     "AZEITONA",
  //     "OREGANO",
  //     "CEBOLA",
  //   ],
  //   prices: { G: 43.0 },
  // },
  // {
  //   id: 30,
  //   name: "PORTUGUESA DA CASA + Guaraná Antártica 1L",
  //   category: "PROMOÇÃO",
  //   ingredients: [
  //     "MOLHO DE TOMATE",
  //     "MUSSARELA",
  //     "PRESUNTO",
  //     "CALABRESA",
  //     "OVO",
  //     "CEBOLA",
  //     "PIMENTAO",
  //     "GELEIA DE PIMENTA",
  //     "MILHO VERDE",
  //     "AZEITONA",
  //     "OREGANO",
  //   ],
  //   prices: { G: 43.0 },
  // },
  // {
  //   id: 31,
  //   name: "PIZZA MARGHERITA + Guaraná Antártica 1L",
  //   category: "PROMOÇÃO",
  //   ingredients: [
  //     "MOLHO DE TOMATE",
  //     "MUSSARELA",
  //     "TOMATE",
  //     "MANJERICÃO",
  //     "AZEITE DE OLIVA",
  //     "AZEITONA",
  //     "OREGANO",
  //   ],
  //   prices: { G: 43.0 },
  // },
  // {
  //   id: 32,
  //   name: "PIZZA DE FRANGO + Guaraná Antártica 1L",
  //   category: "PROMOÇÃO",
  //   ingredients: [
  //     "MOLHO DE TOMATE ESPECIAL",
  //     "MUSSARELA",
  //     "FRANGO",
  //     "MILHO VERDE",
  //     "AZEITONAS",
  //     "OREGANO",
  //   ],
  //   prices: { G: 43.0 },
  // },
]);

const edges = ref([
  { id: 1, name: "BORDA DE CATUPIRY ORIGINAL", price: 15.0 },
  { id: 2, name: "BORDA CHEDDAR ORIGINAL", price: 15.0 },
  { id: 3, name: "BORDA CREAM CHEESE ORIGINAL", price: 15.0 },
  { id: 4, name: "BORDA DE CHOCOLATE AO LEITE", price: 15.0 },
  { id: 5, name: "BORDA DE CHOCOLATE BRANCO", price: 15.0 },
]);

const additionals = ref([
  { id: 1, name: "CATUPIRY ORIGINAL", price: 10.0 },
  { id: 2, name: "CHEDDAR", price: 10.0 },
  { id: 3, name: "CREM CHEESE", price: 10.0 },
  { id: 4, name: "GELEIA DE PIMENTA", price: 5.0 },
]);

const selectedPizza = ref(null);
const selectedSize = ref("P");
const selectedEdge = ref(null);
const selectedAdditionals = ref([]);
const selectedComment = ref("");
const selectedFlavors = ref([]);
const cart = ref([]);
const categoryFilter = ref("TODAS");
const isCartOpen = ref(false);
const isCheckoutOpen = ref(false);

const selectPizza = (pizza) => {
  selectedPizza.value = pizza;
  if (pizza.category === "BEBIDA") {
    selectedSize.value = null;
  } else if (pizza.category === "PROMOÇÃO") {
    selectedSize.value = "G";
  } else {
    selectedSize.value = "P";
  }
  selectedEdge.value = null;
  selectedAdditionals.value = [];
  selectedComment.value = "";
  selectedFlavors.value = [];
};

const addToCart = () => {
  if (selectedPizza.value) {
    const isBeverage = selectedPizza.value.category === "BEBIDA";
    const isPromotion = selectedPizza.value.category === "PROMOÇÃO";
    let itemPrice = isBeverage
      ? selectedPizza.value.prices.unit
      : selectedPizza.value.prices[selectedSize.value];

    // Se tamanho G e há sabores selecionados (meio a meio), somar metade da pizza base + metade de cada sabor
    if (
      selectedSize.value === "G" &&
      selectedFlavors.value.length > 0 &&
      !isBeverage &&
      !isPromotion
    ) {
      const basePrice = selectedPizza.value.prices[selectedSize.value] / 2;
      const totalFlavorPrice = selectedFlavors.value.reduce(
        (sum, flavor) => sum + flavor.prices[selectedSize.value] / 2,
        0,
      );
      itemPrice = basePrice + totalFlavorPrice;
    }
    // Se tamanho G sem sabores adicionais, usa o preço normal (não divide)

    if (selectedEdge.value && !isBeverage) {
      itemPrice += selectedEdge.value.price;
    }

    // Adicionar preço dos adicionais
    if (selectedAdditionals.value.length > 0 && !isBeverage) {
      const additionalsPrice = selectedAdditionals.value.reduce(
        (sum, additional) => sum + additional.price,
        0,
      );
      itemPrice += additionalsPrice;
    }

    cart.value.push({
      id: Date.now(),
      pizza: selectedPizza.value,
      size: isBeverage ? null : selectedSize.value,
      edge: selectedEdge.value,
      additionals:
        selectedAdditionals.value.length > 0
          ? [...selectedAdditionals.value]
          : null,
      price: itemPrice,
      comment: selectedComment.value,
      flavors:
        selectedFlavors.value.length > 0 ? [...selectedFlavors.value] : null,
    });
    selectedPizza.value = null;
    selectedEdge.value = null;
    selectedAdditionals.value = [];
    selectedComment.value = "";
    selectedFlavors.value = [];
  }
};

const removeFromCart = (id) => {
  cart.value = cart.value.filter((item) => item.id !== id);
};

const getTotalPrice = () => {
  return cart.value.reduce((total, item) => total + item.price, 0);
};

const getFilteredPizzas = () => {
  if (categoryFilter.value === "TODAS") {
    return pizzas.value;
  }
  return pizzas.value.filter(
    (p) => (p.category || "TRADICIONAL") === categoryFilter.value,
  );
};

const getAvailableSizes = (pizza) => {
  if (pizza.category === "PROMOÇÃO") {
    return ["G"];
  }
  return ["P", "G"];
};

const handleCompleteOrder = (order) => {
  console.log("Pedido finalizado:", order);
  cart.value = [];
  isCheckoutOpen.value = false;
  isCartOpen.value = false;
};

const getPaymentMethodLabel = (method) => {
  const labels = {
    pix: "PIX",
    credit: "Cartão de Crédito",
    debit: "Cartão de Débito",
    cash: "Dinheiro",
  };
  return labels[method] || method;
};
</script>

<template>
  <div class="pizzaria-app">
    <img src="/logo.png" alt="" />
    <div class="container">
      <div class="main-content">
        <section class="pizzas-section">
          <div class="section-header">
            <h2>Nossas Pizzas</h2>
            <div class="filter-buttons">
              <button
                v-for="category in [
                  'TODAS',
                  // 'PROMOÇÃO',
                  'TRADICIONAL',
                  'ESPECIAL',
                  'DOCE',
                  'BEBIDA',
                ]"
                :key="category"
                :class="[
                  'filter-btn',
                  {
                    active: categoryFilter === category,
                    promo: category === 'PROMOÇÃO',
                  },
                ]"
                @click="categoryFilter = category"
              >
                <span v-if="category === 'PROMOÇÃO'" class="promo-badge"
                  >SÓ HOJE</span
                >
                <span v-if="category === 'PROMOÇÃO'" class="fire-icon">🔥</span>
                {{ category }}
              </button>
            </div>
          </div>
          <PizzaList
            :pizzas="getFilteredPizzas()"
            @select-pizza="selectPizza"
          />
        </section>

        <section class="detail-section" v-if="selectedPizza">
          <PizzaDetail
            :pizza="selectedPizza"
            :pizzas="pizzas"
            :sizes="getAvailableSizes(selectedPizza)"
            :edges="edges"
            :additionals="additionals"
            v-model:selectedSize="selectedSize"
            v-model:selectedEdge="selectedEdge"
            v-model:selectedAdditionals="selectedAdditionals"
            v-model:selectedComment="selectedComment"
            v-model:selectedFlavors="selectedFlavors"
            @add-to-cart="addToCart"
            @close="selectedPizza = null"
          />
        </section>
      </div>
    </div>

    <!-- Carrinho Flutuante Fixo no Canto Inferior -->
    <div
      v-if="cart.length > 0"
      class="floating-cart"
      @click="isCartOpen = true"
    >
      <div class="cart-total-display">
        <span class="cart-price">R$ {{ getTotalPrice().toFixed(2) }}</span>
      </div>
      <span class="cart-icon">🛒</span>
    </div>

    <!-- Modal do Carrinho Completo -->
    <div
      v-if="isCartOpen"
      class="cart-modal-overlay"
      @click="isCartOpen = false"
    >
      <div class="cart-modal" @click.stop>
        <button class="modal-close" @click="isCartOpen = false">✕</button>

        <h1>Seu Carrinho</h1>

        <div class="modal-cart-items">
          <div v-if="cart.length === 0" class="empty-cart">
            <p>Carrinho vazio</p>
          </div>
          <div v-else>
            <div v-for="item in cart" :key="item.id" class="modal-cart-item">
              <div class="item-details">
                <p v-if="item.size" class="item-info">
                  Tamanho: {{ item.size }}
                </p>
                <p v-else class="item-info">Bebida: 1L</p>

                <p
                  class="item-info"
                  v-if="!item.flavors || item.flavors.length === 0"
                >
                  {{ item.pizza.name }}
                </p>

                <div
                  v-if="
                    item.size === 'G' && item.flavors && item.flavors.length > 0
                  "
                  class="item-info"
                >
                  <div>1/2 {{ item.pizza.name }}</div>
                  <div v-for="flavor in item.flavors" :key="flavor.id">
                    1/2 {{ flavor.name }}
                  </div>
                </div>
                <p
                  v-else-if="item.flavors && item.flavors.length > 0"
                  class="item-info"
                >
                  Sabor: {{ item.flavors.map((f) => f.name).join(" + ") }}
                </p>

                <p v-if="item.edge" class="item-info">
                  {{ item.edge.name }} (+R$ {{ item.edge.price.toFixed(2) }})
                </p>
                <div
                  v-if="item.additionals && item.additionals.length > 0"
                  class="item-info"
                >
                  <div
                    v-for="additional in item.additionals"
                    :key="additional.id"
                  >
                    {{ additional.name }} (+R$
                    {{ additional.price.toFixed(2) }})
                  </div>
                </div>
                <p v-if="item.comment" class="item-comment">
                  💬 {{ item.comment }}
                </p>
              </div>
              <div class="item-actions">
                <span class="price">R$ {{ item.price.toFixed(2) }}</span>
                <button
                  @click="removeFromCart(item.id)"
                  class="remove-btn-modal"
                >
                  Remover
                </button>
              </div>
            </div>

            <div class="modal-cart-summary">
              <div class="summary-row">
                <span>Subtotal:</span>
                <span>R$ {{ getTotalPrice().toFixed(2) }}</span>
              </div>
              <div class="summary-row total">
                <span>Total:</span>
                <span>R$ {{ getTotalPrice().toFixed(2) }}</span>
              </div>
              <button
                class="checkout-btn"
                @click="
                  isCheckoutOpen = true;
                  isCartOpen = false;
                "
              >
                Finalizar Pedido
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Modal de Checkout -->
    <div
      v-if="isCheckoutOpen"
      class="checkout-modal-overlay"
      @click="isCheckoutOpen = false"
    >
      <div class="checkout-modal" @click.stop>
        <button class="modal-close" @click="isCheckoutOpen = false">✕</button>
        <CheckoutForm
          :totalPrice="getTotalPrice()"
          :cartItems="cart"
          @complete-order="handleCompleteOrder"
          @back-to-cart="
            isCheckoutOpen = false;
            isCartOpen = true;
          "
        />
      </div>
    </div>

    <!-- Footer -->
    <footer class="pizzaria-footer">
      <div class="footer-content">
        <p class="footer-title">Horário de Funcionamento</p>
        <p class="footer-text">SÁBADOS E DOMINGOS</p>
        <p class="footer-text">DE 18HS ÀS 22:30HS</p>
      </div>
    </footer>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.pizzaria-app {
  min-height: 100vh;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.pizzaria-app img {
  width: 200px;
  display: block;
  margin: 0 auto;
}

.header {
  background: #e8383f;
  color: rgb(255, 255, 255);
  padding: 2rem;
  text-align: center;
  border-bottom: 6px solid #8b0e0e;
}

.header h1 {
  font-size: 3rem;
  margin-bottom: 0.5rem;
}

.subtitle {
  font-size: 1.2rem;
  opacity: 0.9;
}

.container {
  display: flex;
  max-width: 1400px;
  margin: 2rem auto;
  gap: 2rem;
  padding: 0 2rem;
}

.main-content {
  flex: 1;
  min-width: 0;
}

.section-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 1.5rem;
  margin-bottom: 1.5rem;
}

.pizzas-section h2 {
  color: black;
  font-size: 1.8rem;
  margin: 0;
}

.filter-buttons {
  display: flex;
  gap: 0.8rem;
  flex-wrap: wrap;
}

.filter-btn {
  background: white;
  color: black;
  border: 2px solid #c61818;
  padding: 0.6rem 1.2rem;
  border-radius: 20px;
  cursor: pointer;
  transition: all 0.3s;
  font-weight: 600;
  font-size: 0.9rem;
  position: relative;
}

.filter-btn.promo {
  background: linear-gradient(135deg, #ff4500 0%, #ff6347 100%);
  color: #ffffff;
  border: 2px solid #ff4500;
  padding: 0.6rem 1.2rem 0.6rem 2.5rem;
  font-weight: 700;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
  box-shadow: 0 4px 15px rgba(255, 69, 0, 0.4);
}

.filter-btn.promo:hover {
  transform: scale(1.05);
  box-shadow: 0 6px 20px rgba(255, 69, 0, 0.6);
}

.promo-badge {
  position: absolute;
  top: -8px;
  right: -8px;
  background: #ff0000;
  color: white;
  font-size: 0.65rem;
  padding: 0.2rem 0.5rem;
  border-radius: 10px;
  font-weight: 700;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.3);
  animation: pulse 1.5s ease-in-out infinite;
}

@keyframes pulse {
  0%,
  100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.1);
  }
}

.fire-icon {
  position: absolute;
  left: 0.7rem;
  top: 50%;
  transform: translateY(-50%);
  font-size: 1.2rem;
  animation: flicker 1s ease-in-out infinite;
}

@keyframes flicker {
  0%,
  100% {
    opacity: 1;
    transform: translateY(-50%) scale(1);
  }
  50% {
    opacity: 0.8;
    transform: translateY(-50%) scale(1.1);
  }
}

.filter-btn.active {
  background: #c61818;
  border-color: #c61818;
  color: white;
  box-shadow: 0 4px 15px rgba(198, 24, 24, 0.3);
}

.filter-btn.promo.active {
  background: linear-gradient(135deg, #cc3700 0%, #ff4500 100%);
  border-color: #cc3700;
  transform: scale(1.05);
}

.detail-section {
  margin-top: 2rem;
}

/* Carrinho Flutuante */
.floating-cart {
  position: fixed;
  bottom: 2rem;
  right: 2rem;
  background: #e8383f;
  color: white;
  padding: 1rem 1.5rem;
  border-radius: 50px;
  cursor: pointer;
  box-shadow: 0 8px 24px rgba(198, 24, 24, 0.4);
  display: flex;
  align-items: center;
  gap: 1rem;
  transition: all 0.3s ease;
  z-index: 99;
  backdrop-filter: blur(8px);
}

.floating-cart:hover {
  transform: translateY(-5px);
  box-shadow: 0 12px 32px rgba(198, 24, 24, 0.5);
}

.floating-cart:active {
  transform: translateY(-2px);
}

.cart-total-display {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 0.3rem;
}

.cart-count {
  font-size: 0.75rem;
  opacity: 0.9;
  font-weight: 500;
}

.cart-price {
  font-size: 1.1rem;
  font-weight: 700;
}

.cart-icon {
  font-size: 1.5rem;
  animation: bounce 0.6s ease infinite;
}

@keyframes bounce {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-4px);
  }
}

/* Modal do Carrinho */
.cart-modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.6);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  padding: 5px;
  animation: fadeIn 0.3s ease;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.cart-modal {
  background: rgba(255, 255, 255, 0.95);
  border-radius: 16px;
  max-width: 600px;
  width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
  position: relative;
  animation: slideUp 0.3s ease;
  padding: 2rem;
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(50px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.modal-close {
  position: absolute;
  top: 1.5rem;
  right: 1.5rem;
  background: #f0f0f0;
  color: #333;
  border: none;
  cursor: pointer;
  font-size: 1.5rem;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s;
}

.modal-close:hover {
  color: white;
}

.cart-modal h1 {
  background: #e8383f;
  color: rgb(255, 255, 255);
  margin: 0;
  padding: 2rem;
  font-size: 1.8rem;
  border-bottom: 4px solid #8b0e0e;
  margin-bottom: 1.5rem;
}

.modal-cart-items {
  margin-bottom: 2rem;
}

.modal-cart-item {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  padding: 1rem;
  border: 2px solid #ffcccc;
  border-left: 4px solid #c61818;
  border-radius: 8px;
  margin-bottom: 1rem;
  gap: 1rem;
  background: #fef5f5;
}

.item-details h3 {
  color: black;
  font-size: 1rem;
  margin-bottom: 0.5rem;
}

.item-details .item-info {
  color: #333;
  font-size: 0.85rem;
  margin: 0.2rem 0;
}

.item-details .item-comment {
  color: #666;
  font-size: 0.85rem;
  margin: 0.5rem 0 0 0;
  padding: 0.5rem 0.8rem;
  background: #f9f9f9;
  border-left: 3px solid #c61818;
  border-radius: 4px;
  font-style: italic;
}

.item-actions {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 0.5rem;
  min-width: 100px;
}

.item-actions .price {
  font-size: 1.1rem;
  font-weight: 700;
  color: #c61818;
}

.remove-btn-modal {
  background: #f5f5f5;
  color: #c61818;
  border: 1px solid #ddd;
  padding: 0.5rem 1rem;
  border-radius: 6px;
  cursor: pointer;
  font-size: 0.85rem;
  font-weight: 600;
  transition: all 0.3s;
}

.remove-btn-modal:hover {
  background: #c61818;
  color: white;
  border-color: #c61818;
}

.modal-cart-summary {
  background: #ffecec;
  border-radius: 8px;
  border-top: 2px solid #c61818;
}

.summary-row {
  display: flex;
  justify-content: space-between;
  padding: 0.7rem 0;
  color: black;
  font-size: 0.95rem;
}

.summary-row.total {
  border-top: 2px solid #c61818;
  padding-top: 1rem;
  font-size: 1.2rem;
  font-weight: 700;
  color: black;
  margin-bottom: 1rem;
}

.checkout-btn {
  width: 100%;
  padding: 1rem;
  background: #e8383f;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s;
  box-shadow: 0 4px 15px rgba(198, 24, 24, 0.3);
}

.checkout-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(198, 24, 24, 0.4);
}

.checkout-btn:active {
  transform: translateY(0);
}

@media (max-width: 1024px) {
  .container {
    flex-direction: column;
  }

  .floating-cart {
    bottom: 1.5rem;
    right: 1.5rem;
    padding: 0.9rem 1.2rem;
  }

  .cart-price {
    font-size: 1rem;
  }

  .header h1 {
    font-size: 2rem;
  }

  .section-header {
    flex-direction: column;
    align-items: flex-start;
  }

  .pizzas-section h2 {
    font-size: 1.3rem;
  }
}

@media (max-width: 640px) {
  .container {
    padding: 0 1rem;
  }

  .floating-cart {
    bottom: 1rem;
    right: 1rem;
    padding: 0.8rem 1rem;
  }

  .cart-total-display {
    gap: 0.2rem;
  }

  .cart-count {
    font-size: 0.7rem;
  }

  .cart-price {
    font-size: 0.95rem;
  }

  .cart-icon {
    font-size: 1.2rem;
  }

  .cart-modal {
    max-height: 95vh;
    padding: 1.5rem;
  }

  .header h1 {
    font-size: 1.5rem;
  }

  .pizzas-section h2 {
    font-size: 1.3rem;
  }

  .filter-buttons {
    width: 100%;
    gap: 0.5rem;
  }

  .filter-btn {
    padding: 0.5rem 1rem;
    font-size: 0.85rem;
  }
}

/* Checkout Modal Styles */
.checkout-modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1000;
  padding: 1rem;
  backdrop-filter: blur(4px);
}

.checkout-modal {
  background: white;
  border-radius: 12px;
  max-width: 600px;
  width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  position: relative;
  animation: slideUp 0.3s ease-out;
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.modal-close {
  position: absolute;
  top: 1.5rem;
  right: 1.5rem;
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  color: #999;
  transition: color 0.3s;
  z-index: 10;
}

.modal-close:hover {
  color: #c61818;
}

@media (max-width: 768px) {
  .checkout-modal {
    max-height: 95vh;
    border-radius: 16px 16px 0 0;
  }
}

/* Footer Styles */
.pizzaria-footer {
  background: #e8383f;
  color: white;
  padding: 2rem;
  text-align: center;
  border-top: 6px solid #8b0e0e;
  margin-top: 3rem;
}

.footer-content {
  max-width: 1400px;
  margin: 0 auto;
}

.footer-title {
  font-size: 1.3rem;
  font-weight: 700;
  margin-bottom: 1rem;
  text-transform: uppercase;
}

.footer-text {
  font-size: 1.1rem;
  margin: 0.5rem 0;
  font-weight: 600;
}
</style>
