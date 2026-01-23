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

      <aside class="cart-section">
        <h2>Carrinho</h2>
        <div class="cart-items">
          <div v-if="cart.length === 0" class="empty-cart">
            <p>Carrinho vazio</p>
          </div>
          <div v-else>
            <div v-for="item in cart" :key="item.id" class="cart-item">
              <div class="item-info">
                <p class="item-name">{{ item.pizza.name }}</p>
                <p v-if="item.size" class="item-size">{{ item.size }}cm</p>
                <p v-else class="item-size">1L</p>
                <p v-if="item.edge" class="item-edge">{{ item.edge.name }}</p>
              </div>
              <div class="item-price">
                <p>R$ {{ item.price.toFixed(2) }}</p>
                <button @click="removeFromCart(item.id)" class="remove-btn">
                  ✕
                </button>
              </div>
            </div>
            <div class="cart-total">
              <h3>Total: R$ {{ getTotalPrice().toFixed(2) }}</h3>
            </div>
          </div>
        </div>
      </aside>
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
  background: #2e2e32;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.header {
  background: #2e2e32;
  color: #fff;
  padding: 2rem;
  text-align: center;
  border-bottom: 4px solid #c61818;
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
  color: #fff;
  font-size: 1.8rem;
  margin: 0;
}

.filter-buttons {
  display: flex;
  gap: 0.8rem;
  flex-wrap: wrap;
}

.filter-btn {
  background: rgba(255, 255, 255, 0.2);
  color: #fff;
  border: 2px solid rgba(255, 255, 255, 0.4);
  padding: 0.6rem 1.2rem;
  border-radius: 20px;
  cursor: pointer;
  transition: all 0.3s;
  font-weight: 600;
  font-size: 0.9rem;
}

.filter-btn.active {
  background: rgba(255, 255, 255, 0.3);
  border-color: rgba(255, 255, 255, 0.6);
}

.filter-btn.active {
  background: #c61818;
  border-color: #c61818;
  box-shadow: 0 4px 15px rgba(198, 24, 24, 0.3);
}

.detail-section {
  margin-top: 2rem;
}

.cart-section {
  width: 320px;
  background: rgba(255, 255, 255, 0.95);
  border-radius: 12px;
  padding: 1.5rem;
  height: fit-content;
  position: sticky;
  top: 2rem;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);
}

.cart-items {
  max-height: 500px;
  overflow-y: auto;
}

.empty-cart {
  text-align: center;
  color: #999;
  padding: 2rem 1rem;
}

.cart-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
  border-bottom: 1px solid #eee;
  gap: 1rem;
}

.item-info {
  flex: 1;
  min-width: 0;
}

.item-name {
  font-size: 0.9rem;
  font-weight: 600;
  color: #333;
  margin-bottom: 0.3rem;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.item-size {
  font-size: 0.8rem;
  color: #666;
}

.item-edge {
  font-size: 0.75rem;
  color: #c61818;
  font-weight: 600;
  margin-top: 0.2rem;
}

.item-price {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 0.5rem;
}

.item-price p {
  font-weight: 600;
  color: #c61818;
}

.remove-btn {
  background: #c61818;
  color: white;
  border: none;
  width: 24px;
  height: 24px;
  border-radius: 50%;
  cursor: pointer;
  font-size: 0.8rem;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.3s;
}

.remove-btn:hover {
  background: #8b0e0e;
}

.cart-total {
  padding: 1rem;
  background: #f8f8f8;
  border-radius: 8px;
  margin-top: 1rem;
  border-top: 2px solid #c61818;
}

.cart-total h3 {
  color: #333;
  text-align: right;
}

@media (max-width: 1024px) {
  .container {
    flex-direction: column;
  }

  .cart-section {
    width: 100%;
    position: static;
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

  .header h1 {
    font-size: 1.5rem;
  }

  .pizzas-section h2,
  .cart-section h2 {
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
