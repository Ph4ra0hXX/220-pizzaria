<script setup>
import { ref } from "vue";
import PizzaList from "./components/PizzaList.vue";
import PizzaDetail from "./components/PizzaDetail.vue";

const pizzas = ref([
  {
    id: 1,
    name: "PIZZA DE MUSSARELA",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 37.0, 35: 48.0 },
  },
  {
    id: 2,
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
    prices: { 25: 37.0, 35: 48.0 },
  },
  {
    id: 3,
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
    prices: { 25: 37.0, 35: 48.0 },
  },
  {
    id: 4,
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
    prices: { 25: 37.0, 35: 48.0 },
  },
  {
    id: 5,
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
    prices: { 25: 39.0, 35: 50.0 },
  },
  {
    id: 6,
    name: "PIZZA DE MARGUERITA",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "TOMATE",
      "MANJERICÃO",
      "AZEITE DE OLIVA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 37.0, 35: 48.0 },
  },
  {
    id: 7,
    name: "PIZZA MISTA",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "PRESUNTO",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 37.0, 35: 48.0 },
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
    prices: { 25: 37.0, 35: 48.0 },
  },
  {
    id: 9,
    name: "PIZZA NAPOLITANA",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "TOMATE",
      "ALHO TORRADO",
      "QUEIJO PARMESÃO",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 37.0, 35: 48.0 },
  },
  {
    id: 10,
    name: "PIZZA DE PALMITO",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "PALMITO",
      "CEBOLA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 37.0, 35: 48.0 },
  },
  {
    id: 11,
    name: "PIZZA DE LOMBINHO",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "LOMBINHO",
      "CEBOLA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 40.0, 35: 50.0 },
  },
  {
    id: 12,
    name: "PIZZA PEPPERONI",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "PEPPERONI",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 40.0, 35: 50.0 },
  },
  {
    id: 13,
    name: "PIZZA DE CARNE DO SOL",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "CARNE DO SOL",
      "CEBOLA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 42.0, 35: 52.0 },
  },
  {
    id: 14,
    name: "PIZZA DE CARNE DO SOL COM CATUPIRY",
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
    prices: { 25: 44.0, 35: 54.0 },
  },
  {
    id: 15,
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
    prices: { 25: 39.0, 35: 50.0 },
  },
  {
    id: 16,
    name: "FRANBACON DA CASA",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "FRANGO",
      "BACON",
      "MILHO VERDE",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 41.0, 35: 54.0 },
  },
  {
    id: 17,
    name: "FRANBACON C/ CATUPIRY DA CASA",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "FRANGO",
      "BACON",
      "CATUPIRY",
      "MILHO VERDE",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 43.0, 35: 56.0 },
  },
  {
    id: 18,
    name: "BACON DA CASA",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "BACON",
      "TOMATE CEREJA",
      "GELEIA DE PIMENTA",
      "MANJERICÃO",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 41.0, 35: 54.0 },
  },
  {
    id: 19,
    name: "PORTUGUESA DA CASA",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "PRESUNTO",
      "CALABRESA PICADA",
      "OVO",
      "CEBOLA",
      "PIMENTÃO",
      "GELEIA DE PIMENTA",
      "MILHO VERDE",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 43.0, 35: 56.0 },
  },
  {
    id: 20,
    name: "CAMARÃO DA CASA",
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
    prices: { 25: 44.0, 35: 60.0 },
  },
  {
    id: 21,
    name: "CAMARÃO C/ CATUPIRY DA CASA",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "CAMARÃO REFOGADO",
      "CATUPIRY",
      "ALHO TORRADO",
      "FOLHA DE MANJERICÃO",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 46.0, 35: 62.0 },
  },
  {
    id: 22,
    name: "CARNE DO SOL DA CASA",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "CARNE DO SOL",
      "QUEIJO COALHO EM CUBOS",
      "CEBOLA",
      "PIMENTÃO",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 44.0, 35: 60.0 },
  },
  {
    id: 23,
    name: "CARNE DO SOL C/ CATUPIRY DA CASA",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "CARNE DO SOL",
      "QUEIJO COALHO EM CUBOS",
      "CATUPIRY",
      "CEBOLA",
      "PIMENTÃO",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 44.0, 35: 60.0 },
  },
  {
    id: 24,
    name: "FILÉ DA CASA",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "FILÉ",
      "GELEIA DE PIMENTA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 48.0, 35: 68.0 },
  },
  {
    id: 25,
    name: "LOMBINHO C/ ABACAXI DA CASA",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "LOMBINHO",
      "ABACAXI CARAMELIZADO",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { 25: 46.0, 35: 62.0 },
  },
  {
    id: 26,
    name: "DISQUETE",
    category: "DOCE",
    ingredients: ["CHOCOLATE AO LEITE", "DISQUETES"],
    prices: { 25: 37.0, 35: 48.0 },
  },
  {
    id: 27,
    name: "CHARGE",
    category: "DOCE",
    ingredients: [
      "CHOCOLATE AO LEITE",
      "CHOCOLATE CHARGE",
      "AMENDOIM TRITURADO",
    ],
    prices: { 25: 37.0, 35: 48.0 },
  },
  {
    id: 28,
    name: "COCA COLA 1L",
    category: "BEBIDA",
    ingredients: [],
    prices: { unit: 10.0 },
  },
  {
    id: 29,
    name: "COCA ZERO 1L",
    category: "BEBIDA",
    ingredients: [],
    prices: { unit: 12.0 },
  },
  {
    id: 30,
    name: "GUARANA ANTARTICA 1L",
    category: "BEBIDA",
    ingredients: [],
    prices: { unit: 10.0 },
  },
  {
    id: 31,
    name: "GUARANA ZERO 1L",
    category: "BEBIDA",
    ingredients: [],
    prices: { unit: 12.0 },
  },
  {
    id: 32,
    name: "CAJUINA 1L",
    category: "BEBIDA",
    ingredients: [],
    prices: { unit: 10.0 },
  },
]);

const edges = ref([
  { id: 1, name: "BORDA DE CATUPIRY ORIGINAL", price: 13.0 },
  { id: 2, name: "BORDA CHEDDAR ORIGINAL", price: 13.0 },
  { id: 3, name: "BORDA CREAM CHEESE ORIGINAL", price: 15.0 },
  { id: 4, name: "BORDA DE CHOCOLATE AO LEITE", price: 15.0 },
  { id: 5, name: "BORDA DE CHOCOLATE BRANCO", price: 15.0 },
]);

const selectedPizza = ref(null);
const selectedSize = ref(25);
const selectedEdge = ref(null);
const cart = ref([]);
const categoryFilter = ref("TODAS");
const isCartOpen = ref(false);

const selectPizza = (pizza) => {
  selectedPizza.value = pizza;
  selectedSize.value = pizza.category === "BEBIDA" ? null : 25;
  selectedEdge.value = null;
};

const addToCart = () => {
  if (selectedPizza.value) {
    const isBeverage = selectedPizza.value.category === "BEBIDA";
    let itemPrice = isBeverage
      ? selectedPizza.value.prices.unit
      : selectedPizza.value.prices[selectedSize.value];

    if (selectedEdge.value && !isBeverage) {
      itemPrice += selectedEdge.value.price;
    }

    cart.value.push({
      id: Date.now(),
      pizza: selectedPizza.value,
      size: isBeverage ? null : selectedSize.value,
      edge: selectedEdge.value,
      price: itemPrice,
    });
    selectedPizza.value = null;
    selectedEdge.value = null;
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
</script>

<template>
  <div class="pizzaria-app">
    <header class="header">
      <h1>🍕 PIZZARIA</h1>
      <p class="subtitle">Cardápio Completo</p>
    </header>

    <div class="container">
      <div class="main-content">
        <section class="pizzas-section">
          <div class="section-header">
            <h2>Nossas Pizzas</h2>
            <div class="filter-buttons">
              <button
                v-for="category in [
                  'TODAS',
                  'TRADICIONAL',
                  'ESPECIAL',
                  'DOCE',
                  'BEBIDA',
                ]"
                :key="category"
                :class="['filter-btn', { active: categoryFilter === category }]"
                @click="categoryFilter = category"
              >
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
            :sizes="[25, 35]"
            :edges="edges"
            v-model:selectedSize="selectedSize"
            v-model:selectedEdge="selectedEdge"
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
        <span class="cart-count">{{ cart.length }}</span>
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
                <h3>{{ item.pizza.name }}</h3>
                <p v-if="item.size" class="item-info">
                  Tamanho: {{ item.size }}cm
                </p>
                <p v-else class="item-info">Bebida: 1L</p>
                <p v-if="item.edge" class="item-info">{{ item.edge.name }}</p>
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
              <button class="checkout-btn">Finalizar Pedido</button>
            </div>
          </div>
        </div>
      </div>
    </div>
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
  background: white;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.header {
  background: linear-gradient(135deg, #c61818 0%, #e8383f 100%);
  color: black;
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
  background: white;
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
}

.filter-btn.active {
  background: #c61818;
  border-color: #c61818;
  color: white;
  box-shadow: 0 4px 15px rgba(198, 24, 24, 0.3);
}

.detail-section {
  margin-top: 2rem;
}

/* Carrinho Flutuante */
.floating-cart {
  position: fixed;
  bottom: 2rem;
  right: 2rem;
  background: linear-gradient(135deg, #c61818 0%, #e8383f 100%);
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
  background: white;
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
  background: #c61818;
  color: white;
}

.cart-modal h1 {
  background: linear-gradient(135deg, #c61818 0%, #e8383f 100%);
  color: black;
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
  background: linear-gradient(135deg, #fff8f8 0%, #ffecec 100%);
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
  background: linear-gradient(135deg, #c61818 0%, #e8383f 100%);
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
</style>
