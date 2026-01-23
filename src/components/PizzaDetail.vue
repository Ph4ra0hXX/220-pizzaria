<script setup>
const props = defineProps({
  pizza: {
    type: Object,
    required: true,
  },
  sizes: {
    type: Array,
    default: () => [25, 35],
  },
  selectedSize: {
    type: Number,
    required: true,
  },
  edges: {
    type: Array,
    default: () => [],
  },
  selectedEdge: {
    type: Object,
    default: null,
  },
});

defineEmits([
  "update:selectedSize",
  "update:selectedEdge",
  "add-to-cart",
  "close",
]);

const isBeverage = (pizza) => {
  return pizza.category === "BEBIDA";
};

const getPrice = (pizza, size) => {
  if (isBeverage(pizza)) {
    return pizza.prices.unit.toFixed(2);
  }
  return pizza.prices[size].toFixed(2);
};

const getDisplayPrice = (pizza, edge) => {
  if (isBeverage(pizza)) {
    return pizza.prices.unit.toFixed(2);
  }
  let price = parseFloat(getPrice(pizza, props.selectedSize));
  if (edge) {
    price += edge.price;
  }
  return price.toFixed(2);
};
</script>

<template>
  <div class="detail-container">
    <div class="detail-card">
      <button class="close-btn" @click="$emit('close')">✕</button>

      <div class="detail-header">
        <div class="pizza-icon" :class="{ 'beverage-icon': isBeverage(pizza) }">
          {{ isBeverage(pizza) ? "🥤" : "🍕" }}
        </div>
        <h2>{{ pizza.name }}</h2>
      </div>

      <div class="detail-body">
        <div v-if="!isBeverage(pizza)" class="size-selector">
          <h3>Selecione o tamanho:</h3>
          <div class="size-options">
            <button
              v-for="size in sizes"
              :key="size"
              :class="['size-btn', { active: selectedSize === size }]"
              @click="$emit('update:selectedSize', size)"
            >
              <span class="size-value">{{ size }}cm</span>
              <span class="size-price">R$ {{ getPrice(pizza, size) }}</span>
            </button>
          </div>
        </div>

        <div v-if="!isBeverage(pizza)" class="ingredients-section">
          <h3>Ingredientes:</h3>
          <div class="ingredients-list">
            <span
              v-for="(ingredient, index) in pizza.ingredients"
              :key="index"
              class="ingredient"
            >
              ✓ {{ ingredient }}
            </span>
          </div>
        </div>

        <div
          v-if="!isBeverage(pizza) && edges.length > 0"
          class="edges-section"
        >
          <h3>Bordas (Opcional):</h3>
          <div class="edges-list">
            <button
              class="edge-btn no-edge"
              :class="{ active: !selectedEdge }"
              @click="$emit('update:selectedEdge', null)"
            >
              Sem Borda
            </button>
            <button
              v-for="edge in edges"
              :key="edge.id"
              class="edge-btn"
              :class="{ active: selectedEdge && selectedEdge.id === edge.id }"
              @click="$emit('update:selectedEdge', edge)"
            >
              <span class="edge-name">{{ edge.name }}</span>
              <span class="edge-price">+R$ {{ edge.price.toFixed(2) }}</span>
            </button>
          </div>
        </div>

        <div class="action-section">
          <button class="add-btn" @click="$emit('add-to-cart')">
            Adicionar ao Carrinho - R$
            {{ getDisplayPrice(pizza, selectedEdge) }}
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.detail-container {
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
}

.detail-card {
  background: white;
  border-radius: 16px;
  max-width: 500px;
  width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
  position: relative;
  animation: slideUp 0.3s ease;
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

.close-btn {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: #c61818;
  color: white;
  border: none;
  cursor: pointer;
  font-size: 1.2rem;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.3s;
  z-index: 10;
}

.close-btn:hover {
  background: #8b0e0e;
}

.detail-header {
  background: linear-gradient(135deg, #c61818 0%, #8b0e0e 100%);
  padding: 2rem 1.5rem;
  text-align: center;
  color: white;
}

.pizza-icon {
  font-size: 3.5rem;
  margin-bottom: 1rem;
}

.pizza-icon.beverage-icon {
  animation: bounce 0.6s ease;
}

@keyframes bounce {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

.detail-header h2 {
  font-size: 1.6rem;
  margin: 0;
}

.detail-body {
  padding: 2rem 1.5rem;
}

.size-selector,
.ingredients-section {
  margin-bottom: 2rem;
}

.size-selector h3,
.ingredients-section h3 {
  color: #333;
  font-size: 1.1rem;
  margin-bottom: 1rem;
}

.size-options {
  display: flex;
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.size-btn {
  flex: 1;
  padding: 1rem;
  border: 2px solid #ddd;
  border-radius: 8px;
  background: white;
  cursor: pointer;
  transition: all 0.3s;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}

.size-btn:hover {
  border-color: #c61818;
  background: #fff8f4;
}

.size-btn.active {
  background: #c61818;
  border-color: #c61818;
  color: white;
}

.size-value {
  font-weight: 600;
  font-size: 1rem;
}

.size-price {
  font-size: 0.9rem;
  opacity: 0.8;
}

.ingredients-list {
  display: flex;
  flex-direction: column;
  gap: 0.7rem;
}

.ingredient {
  color: #555;
  font-size: 0.95rem;
  padding: 0.5rem 0.8rem;
  background: #f5f5f5;
  border-radius: 6px;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.edges-section {
  margin-bottom: 2rem;
}

.edges-section h3 {
  color: #333;
  font-size: 1.1rem;
  margin-bottom: 1rem;
}

.edges-list {
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
}

.edge-btn {
  padding: 0.8rem 1rem;
  border: 2px solid #ddd;
  border-radius: 8px;
  background: white;
  cursor: pointer;
  transition: all 0.3s;
  text-align: left;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.edge-btn:hover {
  border-color: #c61818;
  background: #fff8f4;
}

.edge-btn.active {
  background: #c61818;
  border-color: #c61818;
  color: white;
}

.edge-name {
  font-weight: 600;
  flex: 1;
}

.edge-price {
  font-size: 0.9rem;
  opacity: 0.8;
}

.action-section {
  margin-top: 2rem;
  padding-top: 1.5rem;
  border-top: 2px solid #eee;
}

.add-btn {
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

.add-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(255, 107, 53, 0.4);
}

.add-btn:active {
  transform: translateY(0);
}

@media (max-width: 600px) {
  .detail-container {
    padding: 0;
  }

  .detail-card {
    border-radius: 16px 16px 0 0;
    max-height: 95vh;
    margin-left: 5px;
    margin-right: 5px;
  }

  .pizza-icon {
    font-size: 2.5rem;
  }

  .detail-header h2 {
    font-size: 1.3rem;
  }

  .size-options {
    flex-direction: column;
  }
}
</style>
