<script setup>
const props = defineProps({
  pizza: {
    type: Object,
    required: true,
  },
  pizzas: {
    type: Array,
    required: true,
  },
  sizes: {
    type: Array,
    default: () => ["P", "G"],
  },
  selectedSize: {
    type: String,
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
  selectedComment: {
    type: String,
    default: "",
  },
  selectedFlavors: {
    type: Array,
    default: () => [],
  },
});

const emit = defineEmits([
  "update:selectedSize",
  "update:selectedEdge",
  "update:selectedComment",
  "update:selectedFlavors",
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

  // Se tamanho G e há sabores selecionados, usar o preço do sabor mais caro
  if (
    props.selectedSize === "G" &&
    props.selectedFlavors &&
    props.selectedFlavors.length > 0
  ) {
    const maxFlavorPrice = Math.max(
      ...props.selectedFlavors.map(
        (flavor) => flavor.prices[props.selectedSize],
      ),
    );
    price = maxFlavorPrice;
  }

  if (edge) {
    price += edge.price;
  }
  return price.toFixed(2);
};

const getMaxFlavors = () => {
  return 1;
};

const getAvailableFlavors = () => {
  // Retorna todas as pizzas EXCETO a selecionada e bebidas
  return props.pizzas.filter(
    (p) => p.id !== props.pizza.id && p.category !== "BEBIDA",
  );
};

const toggleFlavor = (flavorPizza) => {
  const maxFlavors = getMaxFlavors();
  let newFlavors = [...(props.selectedFlavors || [])];

  const index = newFlavors.findIndex((f) => f.id === flavorPizza.id);
  if (index > -1) {
    // Remove flavor
    newFlavors.splice(index, 1);
  } else {
    // Add flavor if limit not reached
    if (newFlavors.length < maxFlavors) {
      newFlavors.push(flavorPizza);
    }
  }

  emit("update:selectedFlavors", newFlavors);
};

const isFlavorsAllowed = () => {
  return !isBeverage(props.pizza);
};

const isFlavorSelected = (flavorPizza) => {
  return (props.selectedFlavors || []).some((f) => f.id === flavorPizza.id);
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
              <span class="size-value">{{ size }}</span>
              <span class="size-price">R$ {{ getPrice(pizza, size) }}</span>
            </button>
          </div>
        </div>

        <div
          v-if="isFlavorsAllowed() && selectedSize === 'G'"
          class="flavors-section"
        >
          <h3>
            Sabores:
            <span class="flavors-limit">
              ({{ (selectedFlavors || []).length }}/{{ getMaxFlavors() }})
            </span>
          </h3>
          <p v-if="getMaxFlavors() === 1" class="flavor-hint">
            Escolher + um sabor
          </p>
          <div class="flavors-list">
            <button
              v-for="flavorPizza in getAvailableFlavors()"
              :key="flavorPizza.id"
              :class="[
                'flavor-btn',
                {
                  active: isFlavorSelected(flavorPizza),
                  disabled:
                    (selectedFlavors || []).length >= getMaxFlavors() &&
                    !isFlavorSelected(flavorPizza),
                },
              ]"
              @click="toggleFlavor(flavorPizza)"
              :disabled="
                (selectedFlavors || []).length >= getMaxFlavors() &&
                !isFlavorSelected(flavorPizza)
              "
            >
              <span v-if="isFlavorSelected(flavorPizza)" class="check-mark"
                >✓</span
              >
              {{ flavorPizza.name }}
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

        <div class="comment-section">
          <h3>Comentários (Opcional):</h3>
          <textarea
            class="comment-input"
            placeholder="Ex: Sem cebola..."
            :value="selectedComment"
            @input="$emit('update:selectedComment', $event.target.value)"
            maxlength="150"
          ></textarea>
          <p class="char-count">{{ selectedComment.length }}/150</p>
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

.detail-header {
  background: #c61818;
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

.comment-section {
  margin-bottom: 2rem;
}

.comment-section h3 {
  color: #333;
  font-size: 1.1rem;
  margin-bottom: 0.8rem;
}

.comment-input {
  width: 100%;
  padding: 0.8rem;
  border: 2px solid #ddd;
  border-radius: 8px;
  font-size: 0.95rem;
  font-family: inherit;
  resize: vertical;
  min-height: 80px;
  transition: border-color 0.3s;
}

.comment-input:focus {
  outline: none;
  border-color: #c61818;
  background: #fff8f4;
}

.char-count {
  font-size: 0.8rem;
  color: #999;
  margin-top: 0.4rem;
  text-align: right;
}

.action-section {
  margin-top: 2rem;
  padding-top: 1.5rem;
  border-top: 2px solid #eee;
}

.add-btn {
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

.add-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(255, 107, 53, 0.4);
}

.add-btn:active {
  transform: translateY(0);
}

.flavors-section {
  margin-bottom: 2rem;
}

.flavors-section h3 {
  color: #333;
  font-size: 1.1rem;
  margin-bottom: 0.5rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.flavors-limit {
  font-size: 0.85rem;
  color: #c61818;
  font-weight: 700;
}

.flavor-hint {
  color: #666;
  font-size: 0.9rem;
  margin-bottom: 1rem;
  padding: 0.5rem 0.8rem;
  background: #f9f9f9;
  border-left: 3px solid #c61818;
  border-radius: 4px;
}

.flavors-list {
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
}

.flavor-btn {
  padding: 0.8rem 1rem;
  border: 2px solid #ddd;
  border-radius: 8px;
  background: white;
  cursor: pointer;
  transition: all 0.3s;
  text-align: left;
  font-weight: 500;
  color: #333;
  display: flex;
  align-items: center;
  gap: 0.8rem;
}

.flavor-btn:hover:not(.disabled) {
  border-color: #c61818;
  background: #fff8f4;
}

.flavor-btn.active {
  background: #c61818;
  border-color: #c61818;
  color: white;
}

.flavor-btn.disabled {
  opacity: 0.5;
  cursor: not-allowed;
  background: #f5f5f5;
}

.flavor-btn .check-mark {
  font-weight: 700;
  font-size: 1.1rem;
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
