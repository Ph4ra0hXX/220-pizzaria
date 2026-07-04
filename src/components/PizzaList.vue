<script setup>
const props = defineProps({
  pizzas: {
    type: Array,
    required: true,
  },
  appliedCoupon: {
    type: String,
    default: "",
  },
});

defineEmits(["select-pizza"]);

const isBeverage = (pizza) => {
  return pizza.category === "BEBIDA";
};

const getBeveragePrice = (pizza) => {
  if (
    pizza.id === 21 &&
    String(props.appliedCoupon ?? "")
      .trim()
      .toUpperCase() === "DISABLED_COUPON"
  ) {
    return 11.0;
  }

  return pizza.prices.unit;
};

const getIcon = (pizza) => {
  if (isBeverage(pizza)) return "";
  if (pizza.category === "DOCE") return "🍰";
  if (pizza.category === "COMBOS") return "🎁";
  return "🍕";
};

const isEmoji = (str) => {
  return /^[\p{Emoji_Presentation}\p{Extended_Pictographic}]+$/u.test(str);
};

const getPriceDisplay = (pizza) => {
  if (isBeverage(pizza)) {
    return `R$ ${getBeveragePrice(pizza).toFixed(2)}`;
  }
  // Se é COMBO
  if (pizza.category === "COMBOS" && pizza.prices.combo) {
    return `R$ ${pizza.prices.combo.toFixed(2)}`;
  }
  if (pizza.prices.P && pizza.prices.G) {
    return `P: R$ ${pizza.prices.P.toFixed(2)} | G: R$ ${pizza.prices.G.toFixed(2)}`;
  }
  // Se só tem tamanho G (promoção)
  if (pizza.prices.G) {
    return `G: R$ ${pizza.prices.G.toFixed(2)}`;
  }
  // Se só tem tamanho P
  if (pizza.prices.P) {
    return `P: R$ ${pizza.prices.P.toFixed(2)}`;
  }
  return "Preço indisponível";
};

const FEATURED_PIZZA_ID = 221;

const isFeaturedPizza = (pizza) => {
  return pizza.id === FEATURED_PIZZA_ID;
};
</script>

<template>
  <div class="pizza-grid">
    <div
      v-for="pizza in pizzas"
      :key="pizza.id"
      class="pizza-card"
      :class="{ featured: isFeaturedPizza(pizza) }"
      @click="$emit('select-pizza', pizza)"
    >
      <span v-if="isFeaturedPizza(pizza)" class="featured-badge">
        Destaque da casa
      </span>
      <div class="pizza-image">
        <img
          v-if="pizza.image && !isEmoji(pizza.image)"
          :src="pizza.image"
          :alt="pizza.name"
        />
        <div v-else class="pizza-icon">
          {{ isEmoji(pizza.image) ? pizza.image : getIcon(pizza) }}
        </div>
      </div>
      <h3>{{ pizza.name }}</h3>
      <div class="sizes-prices">
        <span class="price-info">{{ getPriceDisplay(pizza) }}</span>
      </div>
      <p v-if="!isBeverage(pizza)" class="ingredients">
        {{ pizza.ingredients.length }} ingredientes
      </p>
      <p v-else class="ingredients">Bebida</p>
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
  position: relative;
  overflow: hidden;
  box-shadow:
    inset 0 30px 30px -15px rgba(255, 255, 255, 0.1),
    inset 0 0 0 1px rgba(255, 255, 255, 0.3),
    inset 0 1px 20px rgba(0, 0, 0, 0),
    0 3px 0 #e8383f,
    0 3px 2px rgba(0, 0, 0, 0.2),
    0 5px 10px rgba(0, 0, 0, 0.1),
    0 10px 20px rgba(0, 0, 0, 0.1);
}

.pizza-card.featured {
  background: linear-gradient(180deg, #fff8f8 0%, #ffffff 52%);
  outline: 2px solid rgba(232, 56, 63, 0.55);
  outline-offset: -2px;
  box-shadow:
    inset 0 30px 30px -15px rgba(255, 255, 255, 0.1),
    inset 0 0 0 1px rgba(255, 255, 255, 0.3),
    inset 0 1px 20px rgba(0, 0, 0, 0),
    0 3px 0 #e8383f,
    0 3px 2px rgba(0, 0, 0, 0.16),
    0 14px 30px rgba(232, 56, 63, 0.26);
}

.pizza-card.featured::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 5px;
  background: linear-gradient(90deg, #c61818, #e8383f);
}

.pizza-card.featured .pizza-image {
  background:
    radial-gradient(circle at center, rgba(232, 56, 63, 0.12), transparent 62%),
    #fff1f1;
  border: 1px solid rgba(232, 56, 63, 0.16);
}

.pizza-card.featured h3 {
  color: #b51418;
  font-weight: 800;
}

.pizza-card.featured .price-info {
  background: rgba(232, 56, 63, 0.1);
  color: #9f1115;
  font-weight: 700;
}

.featured-badge {
  position: absolute;
  top: 1rem;
  left: 1rem;
  z-index: 1;
  background: #e8383f;
  border: 1px solid rgba(255, 255, 255, 0.7);
  border-radius: 999px;
  color: #ffffff;
  font-size: 0.74rem;
  font-weight: 800;
  letter-spacing: 0.03em;
  line-height: 1;
  padding: 0.44rem 0.72rem;
  text-transform: uppercase;
  box-shadow: 0 6px 16px rgba(232, 56, 63, 0.32);
}

.pizza-image {
  width: 100%;
  height: 200px;
  overflow: hidden;
  border-radius: 8px;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #f5f5f5;
}

.pizza-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.pizza-icon {
  font-size: 4rem;
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
