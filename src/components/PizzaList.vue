<script setup>
defineProps({
  pizzas: {
    type: Array,
    required: true,
  },
});

defineEmits(["select-pizza"]);

const isBeverage = (pizza) => {
  return pizza.category === "BEBIDA";
};

const getIcon = (pizza) => {
  if (isBeverage(pizza)) return "🥤";
  if (pizza.category === "DOCE") return "🍰";
  return "🍕";
};

const getPriceDisplay = (pizza) => {
  if (isBeverage(pizza)) {
    return `R$ ${pizza.prices.unit.toFixed(2)}`;
  }
  return `25cm: R$ ${pizza.prices[25].toFixed(2)} | 35cm: R$ ${pizza.prices[35].toFixed(2)}`;
};
</script>

<template>
  <div class="pizza-grid">
    <div
      v-for="pizza in pizzas"
      :key="pizza.id"
      class="pizza-card"
      @click="$emit('select-pizza', pizza)"
    >
      <div class="pizza-icon">{{ getIcon(pizza) }}</div>
      <h3>{{ pizza.name }}</h3>
      <div class="sizes-prices">
        <span class="price-info">{{ getPriceDisplay(pizza) }}</span>
      </div>
      <p v-if="!isBeverage(pizza)" class="ingredients">
        {{ pizza.ingredients.length }} ingredientes
      </p>
      <p v-else class="ingredients">Bebida 1L</p>
    </div>
  </div>
</template>

<style scoped>
.pizza-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 1.5rem;
}

.pizza-card {
  background: rgba(255, 255, 255, 0.95);
  border-radius: 12px;
  padding: 1.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  border: 2px solid transparent;
}

.pizza-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 30px rgba(0, 0, 0, 0.2);
  border-color: #ff6b35;
}

.pizza-icon {
  font-size: 3rem;
  text-align: center;
  margin-bottom: 1rem;
}

.pizza-card h3 {
  color: #333;
  font-size: 1.1rem;
  margin-bottom: 0.8rem;
  text-align: center;
  min-height: 2.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.sizes-prices {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.price-info {
  background: #f0f0f0;
  padding: 0.5rem 0.8rem;
  border-radius: 6px;
  font-size: 0.9rem;
  color: #555;
  text-align: center;
}

.ingredients {
  text-align: center;
  color: #999;
  font-size: 0.9rem;
  margin-top: 0.5rem;
}

@media (max-width: 768px) {
  .pizza-grid {
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 1rem;
  }

  .pizza-card {
    padding: 1rem;
  }

  .pizza-icon {
    font-size: 2rem;
  }

  .pizza-card h3 {
    font-size: 0.95rem;
  }
}
</style>
