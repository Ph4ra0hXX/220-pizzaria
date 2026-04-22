<script setup>
import { ref, computed } from "vue";
import PizzaList from "./components/PizzaList.vue";
import PizzaDetail from "./components/PizzaDetail.vue";
import CheckoutForm from "./components/CheckoutForm.vue";

const pizzas = ref([
  {
    id: 1,
    name: "PIZZA DE CALABRESA SUPREME",
    image: "/pizzas/1.webp",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "CALABRESA",
      "BACON",
      "CEBOLA",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 37.0, G: 48.0 },
  },
  {
    id: 2,
    name: "PIZZA DE FRANGO",
    image: "/pizzas/2.webp",
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
    id: 3,
    image: "/pizzas/3.webp",
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
    id: 99,
    name: "FILÉ MIGNON",
    category: "ESPECIAL",
    image: "/pizzas/19.jpg",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "FILÉ MIGNON",
      "CEBOLA",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 50.0, G: 72.0 },
  },
  {
    id: 4,
    image: "/pizzas/12.webp",
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
    id: 37,
    image: "/pizzas/16.webp",
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
    prices: { P: 37.0, G: 48.0 },
  },
  {
    id: 5,
    image: "/pizzas/5.webp",
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
    id: 6,
    image: "/pizzas/6.webp",
    name: "PIZZA PORTUGUESA DA CASA",
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
    id: 7,
    image: "/pizzas/7.webp",
    name: "PIZZA DE FRANBACON",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "FRANGO",
      "BACON",
      "CEBOLA",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 39.0, G: 52.0 },
  },
  {
    id: 8,
    image: "/pizzas/8.webp",
    name: "PIZZA DE CAMARÃO SUPREME",
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
  {
    id: 9,
    image: "/pizzas/9.webp",
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
    id: 10,
    name: "PIZZA DE LOMBINHO",
    image: "/pizzas/13.webp",
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
    id: 11,
    image: "/pizzas/10.webp",
    name: "PIZZA DE LOMBINHO COM ABACAXI CARAMELIZADO",
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
    id: 12,
    image: "",
    name: "PIZZA DE LOMBINHO COM CATUPIRY",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "LOMBINHO",
      "CATUPIRY",
      "CEBOLA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { P: 42.0, G: 58.0 },
  },
  {
    image: "",
    id: 13,
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
    name: "PIZZA DE FRANGO CHEDDAR",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "FRANGO",
      "MILHO VERDE",
      "CHEDDAR",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 37.0, G: 48.0 },
  },
  {
    id: 15,
    name: "PIZZA DE BACON CHEDDAR",
    category: "TRADICIONAL",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "BACON",
      "MILHO VERDE",
      "CEBOLA",
      "CHEDDAR",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 37.0, G: 48.0 },
  },
  {
    id: 51,
    name: "PIZZA DE BACON",
    category: "TRADICIONAL",
    image: "/pizzas/18.jpg",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "BACON",
      "CEBOLA",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 39.0, G: 50.0 },
  },
  {
    id: 16,
    name: "PIZZA DE DISQUETE",
    image: "/pizzas/15.webp",
    category: "DOCE",
    ingredients: ["CHOCOLATE AO LEITE", "DISQUETES"],
    prices: { P: 39.0, G: 52.0 },
  },
  {
    id: 17,
    name: "PIZZA DE BIS",
    category: "DOCE",
    ingredients: ["CHOCOLATE AO LEITE", "BIS PICADO"],
    image: "",
    prices: { P: 39.0, G: 52.0 },
  },
  {
    id: 18,
    name: "PIZZA DE OURO BRANCO",
    category: "DOCE",
    ingredients: [
      "CHOCOLATE BRANCO",
      "BOMBONS OURO BRANCO",
      "CHOCOLATE AO LEITE",
    ],
    image: "/pizzas/17.webp",
    prices: { P: 45.0, G: 66.0 },
  },
  {
    id: 19,
    name: "COCA COLA 1L",
    category: "BEBIDA",
    image: "/pizzas/bebida1.jpg",
    ingredients: [],
    prices: { unit: 11.0 },
  },
  {
    id: 20,
    name: "COCA ZERO 1L",
    category: "BEBIDA",
    image: "/pizzas/bebida2.jpg",
    ingredients: [],
    prices: { unit: 11.0 },
  },
  {
    id: 21,
    name: "GUARANA ANTARTICA 1L",
    category: "BEBIDA",
    image: "/pizzas/bebida3.jpg",
    ingredients: [],
    prices: { unit: 6.0 },
  },
  {
    id: 22,
    name: "PIZZA DE BACON DA CASA",
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
    image: "",
    prices: { P: 42.0, G: 56.0 },
  },
  {
    id: 23,
    name: "PIZZA DE CARNE DE SOL DA CASA",
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
    image: "/pizzas/11.webp",
    prices: { P: 44.0, G: 66.0 },
  },
  {
    id: 24,
    name: "PIZZA DE ATUM",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE",
      "ATUM",
      "CATUPIRY",
      "MUSSARELA",
      "TOMATE",
      "CEBOLA",
      "AZEITONA",
      "OREGANO",
    ],
    image: "/pizzas/14.webp",
    prices: { P: 44.0, G: 66.0 },
  },
  {
    id: 25,
    image: "/pizzas/20.jpg",
    name: "PIZZA DE PEPPERONI",
    category: "ESPECIAL",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "PEPPERONI",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 42.0, G: 56.0 },
  },
  // {
  //   id: 38,
  //   name: "Pepperoni",
  //   image: "/pizzas/pepperoni.webp",
  //   category: "TRADICIONAL",
  //   ingredients: [
  //     "MOLHO DE TOMATE",
  //     "MUSSARELA",
  //     "PEPPERONI",
  //     "AZEITONA",
  //     "OREGANO",
  //   ],
  //   prices: { P: 40.0, G: 52.0 },
  // },
  {
    id: 39,
    name: "Bacon",
    image: "/pizzas/bacon.webp",
    category: "PROMOCAO",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "BACON",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 40.0, G: 52.0 },
  },
  {
    id: 40,
    name: "Franbacon",
    image: "/pizzas/franbacon.webp",
    category: "PROMOCAO",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "FRANGO",
      "BACON",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 42.0, G: 55.0 },
  },
  {
    id: 41,
    name: "Lombinho",
    image: "/pizzas/lombinho.webp",
    category: "PROMOCAO",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "LOMBINHO",
      "CEBOLA",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { P: 41.0, G: 54.0 },
  },
  {
    id: 65,
    name: "PIZZA DE FRANBACON",
    category: "PROMOÇÃO",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "FRANGO",
      "BACON",
      "CEBOLA",
      "AZEITONA",
      "OREGANO",
    ],
    image: "",
    prices: { G: 36.9 },
  },
  {
    id: 52,
    name: "PIZZA DE MUSSARELA",
    category: "PROMOÇÃO",
    image: "",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { G: 36.9 },
  },
  {
    id: 53,
    name: "PIZZA DE CALABRESA",
    category: "PROMOÇÃO",
    image: "/pizzas/12.webp",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "CALABRESA FATIADA",
      "CEBOLA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { G: 36.9 },
  },
  {
    id: 54,
    name: "PIZZA PORTUGUESA",
    category: "PROMOÇÃO",
    image: "",
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
    prices: { G: 36.9 },
  },
  {
    id: 55,
    name: "PIZZA DE FRANGO",
    category: "PROMOÇÃO",
    image: "/pizzas/2.webp",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "FRANGO",
      "MILHO VERDE",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { G: 36.9 },
  },
  {
    id: 56,
    name: "PIZZA MARGUERITA",
    category: "PROMOÇÃO",
    image: "/pizzas/16.webp",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "TOMATE",
      "MANJERICÃO",
      "AZEITE DE OLIVA",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { G: 36.9 },
  },
  {
    id: 57,
    name: "PIZZA MISTA",
    category: "PROMOÇÃO",
    image: "",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "PRESUNTO",
      "AZEITONA",
      "OREGANO",
      "CEBOLA",
    ],
    prices: { G: 39.9 },
  },
  /*
  {
    id: 58,
    name: "PIZZA DE BACON",
    category: "PROMOÇÃO",
    image: "",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "BACON",
      "CEBOLA",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { G: 39.9 },
  },
  */
  {
    id: 59,
    name: "PIZZA DE LOMBINHO",
    category: "PROMOÇÃO",
    image: "/pizzas/13.webp",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "LOMBINHO",
      "CEBOLA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { G: 39.9 },
  },
  {
    id: 64,
    name: "PIZZA DE CALABRESA SUPREME",
    category: "PROMOÇÃO",
    image: "/pizzas/1.webp",
    ingredients: [
      "MOLHO DE TOMATE",
      "MUSSARELA",
      "CALABRESA",
      "BACON",
      "CEBOLA",
      "AZEITONA",
      "OREGANO",
    ],
    prices: { G: 39.9 },
  },
  {
    id: 66,
    name: "PIZZA DE DISQUETE",
    category: "PROMOÇÃO",
    image: "/pizzas/15.webp",
    ingredients: ["CHOCOLATE AO LEITE", "DISQUETES"],
    prices: { G: 39.9 },
  },
  {
    id: 40,
    name: "PIZZA PORTUGUESA",
    category: "TRADICIONAL",
    image: "",
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
    id: 34,
    name: "PIZZA MISTA",
    category: "TRADICIONAL",
    image: "",
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
    id: 35,
    name: "PIZZA DE FRANGO COM CATUPIRY",
    category: "TRADICIONAL",
    image: "",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "FRANGO",
      "CATUPIRY",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { P: 42.0, G: 58.0 },
  },
  {
    id: 36,
    name: "PIZZA DE MUSSARELA",
    category: "TRADICIONAL",
    image: "",
    ingredients: [
      "MOLHO DE TOMATE ESPECIAL",
      "MUSSARELA",
      "AZEITONAS",
      "OREGANO",
    ],
    prices: { P: 37.0, G: 48.0 },
  },
  {
    id: 60,
    name: "PIZZA G MUSSARELA + PIZZA G DE CALABRESA + GUARANA ANTARTICA 1L",
    category: "COMBOS",
    image: "/pizzas/combo1.webp",
    ingredients: [
      "PIZZA G MUSSARELA",
      "PIZZA G DE CALABRESA",
      "GUARANA ANTARTICA 1L",
    ],
    prices: { combo: 89.9 },
  },
  {
    id: 61,
    name: "PIZZA G FRANGO + PIZZA G CALABRESA + GUARANA ANTARTICA 1L",
    category: "COMBOS",
    image: "/pizzas/combo2.webp",
    ingredients: [
      "PIZZA G FRANGO",
      "PIZZA G CALABRESA",
      "GUARANA ANTARTICA 1L",
    ],
    prices: { combo: 94.9 },
  },
  {
    id: 62,
    name: "PIZZA G CALABRESA + PIZZA G DISQUETE + GUARANA ANTARTICA 1L",
    category: "COMBOS",
    image: "/pizzas/combo3.webp",
    ingredients: [
      "PIZZA G CALABRESA",
      "PIZZA G DISQUETE",
      "GUARANA ANTARTICA 1L",
    ],
    prices: { combo: 99.9 },
  },
  {
    id: 63,
    name: "PIZZA G LOMBINHO C/ABACAXI CARAMELIZADO + PIZZA G MARGUERITA + GUARANA ANTARTICA 1L",
    category: "COMBOS",
    image: "/pizzas/combo4.webp",
    ingredients: [
      "PIZZA G LOMBINHO C/ABACAXI CARAMELIZADO",
      "PIZZA G MARGUERITA",
      "GUARANA ANTARTICA 1L",
    ],
    prices: { combo: 109.9 },
  },
  {
    id: 64,
    name: "PIZZA G CARNE DE SOL + PIZZA G FRANBACON + GUARANA ANTARTICA 1L",
    category: "COMBOS",
    image: "/pizzas/combo5.webp",
    ingredients: [
      "PIZZA G CARNE DE SOL",
      "PIZZA G FRANBACON",
      "GUARANA ANTARTICA 1L",
    ],
    prices: { combo: 109.9 },
  },
]);

const edges = ref([
  { id: 1, name: "BORDA DE CATUPIRY ORIGINAL", price: 15.0 },
  { id: 2, name: "BORDA CHEDDAR ORIGINAL", price: 15.0 },
  { id: 3, name: "BORDA CREAM CHEESE ORIGINAL", price: 15.0 },
  { id: 4, name: "BORDA DE CHOCOLATE AO LEITE", price: 15.0 },
  { id: 5, name: "BORDA DE CHOCOLATE BRANCO", price: 15.0 },
  { id: 6, name: "BORDA DE DOCE DE LEITE", price: 15.0 },
]);

const additionals = ref([
  { id: 1, name: "CATUPIRY ORIGINAL", price: 10.0 },
  { id: 2, name: "CHEDDAR", price: 10.0 },
  { id: 3, name: "CREM CHEESE", price: 10.0 },
  { id: 4, name: "GELEIA DE ABACAXI COM PIMENTA", price: 10.0 },
  { id: 5, name: "GELEIA DE PIMENTA", price: 7.0 },
  { id: 6, name: "ABACAXI CARAMELIZADO", price: 10.0 },
  { id: 7, name: "MILHO VERDE", price: 2.0 },
  { id: 8, name: "CEBOLA", price: 2.0 },
  { id: 9, name: "PIMENTÃO", price: 2.0 },
  { id: 10, name: "TOMATE", price: 2.0 },
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
  } else if (pizza.category === "COMBOS") {
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
    const isCombo = selectedPizza.value.category === "COMBOS";
    let itemPrice = isBeverage
      ? selectedPizza.value.prices.unit
      : isCombo
        ? selectedPizza.value.prices.combo
        : selectedPizza.value.prices[selectedSize.value];

    // Se tamanho G e há sabores selecionados (meio a meio), somar metade da pizza base + metade de cada sabor
    if (
      selectedSize.value === "G" &&
      selectedFlavors.value.length > 0 &&
      !isBeverage &&
      !isPromotion &&
      !isCombo
    ) {
      const basePrice = selectedPizza.value.prices[selectedSize.value] / 2;
      const totalFlavorPrice = selectedFlavors.value.reduce(
        (sum, flavor) => sum + flavor.prices[selectedSize.value] / 2,
        0,
      );
      itemPrice = basePrice + totalFlavorPrice;
    }
    // Se tamanho G sem sabores adicionais, usa o preço normal (não divide)

    if (selectedEdge.value && !isBeverage && !isCombo) {
      itemPrice += selectedEdge.value.price;
    }

    // Adicionar preço dos adicionais
    if (selectedAdditionals.value.length > 0 && !isBeverage && !isCombo) {
      const additionalsPrice = selectedAdditionals.value.reduce(
        (sum, additional) => sum + additional.price,
        0,
      );
      itemPrice += additionalsPrice;
    }

    const newItem = {
      id: Date.now(),
      pizza: selectedPizza.value,
      size: isBeverage || isCombo ? null : selectedSize.value,
      edge: selectedEdge.value,
      additionals:
        selectedAdditionals.value.length > 0
          ? [...selectedAdditionals.value]
          : null,
      price: itemPrice,
      comment: selectedComment.value,
      flavors:
        selectedFlavors.value.length > 0 ? [...selectedFlavors.value] : null,
    };

    cart.value.push(newItem);

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

const getTotalPrice = computed(() => {
  return cart.value.reduce((total, item) => total + item.price, 0);
});

const getFilteredPizzas = () => {
  if (categoryFilter.value === "TODAS") {
    return pizzas.value;
  }
  return pizzas.value.filter(
    (p) => (p.category || "TRADICIONAL") === categoryFilter.value,
  );
};

const getAvailableSizes = (pizza) => {
  if (pizza.category === "COMBOS") {
    return [];
  }
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
                  'PROMOÇÃO',
                  'COMBOS',
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
                    combo: category === 'COMBOS',
                  },
                ]"
                @click="categoryFilter = category"
              >
                <span v-if="category === 'PROMOÇÃO'" class="promo-icon"
                  >💰</span
                >
                <span v-if="category === 'COMBOS'" class="combo-icon">🎁</span>
                <span v-if="category === 'COMBOS'">COMBO COM DESCONTO</span>
                <span v-else>{{ category }}</span>
                <span v-if="category === 'PROMOÇÃO'" class="promo-icon"
                  >💰</span
                >
                <span v-if="category === 'COMBOS'" class="combo-icon">🎁</span>
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
        <span class="cart-price">R$ {{ getTotalPrice.toFixed(2) }}</span>
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
                <p v-if="item.pizza.category === 'COMBOS'" class="item-info">
                  🎁 Combo
                </p>
                <p v-else-if="item.size" class="item-info">
                  Tamanho: {{ item.size }}
                </p>
                <p
                  v-else-if="item.pizza.category === 'BEBIDA'"
                  class="item-info"
                >
                  Bebida: 1L
                </p>

                <p
                  v-if="item.pizza.category === 'COMBOS'"
                  class="item-info combo-name"
                >
                  {{ item.pizza.name }}
                </p>

                <p
                  v-else-if="!item.flavors || item.flavors.length === 0"
                  class="item-info"
                >
                  {{ item.pizza.name }}
                </p>

                <div
                  v-else-if="
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

                <p
                  v-if="item.edge && item.pizza.category !== 'COMBOS'"
                  class="item-info"
                >
                  {{ item.edge.name }}
                  <span v-if="item.edge.price > 0"
                    >(+R$ {{ item.edge.price.toFixed(2) }})</span
                  >
                </p>
                <div
                  v-if="
                    item.additionals &&
                    item.additionals.length > 0 &&
                    item.pizza.category !== 'COMBOS'
                  "
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
              <div class="summary-row total">
                <span>Total:</span>
                <span>R$ {{ getTotalPrice.toFixed(2) }}</span>
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
          :totalPrice="getTotalPrice"
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
  background: linear-gradient(135deg, #ff4e00 0%, #ec9f05 100%);
  color: #ffffff;
  border: 2px solid #ff6b00;
  padding: 0.6rem 1.4rem;
  font-weight: 800;
  font-size: 0.95rem;
  letter-spacing: 0.5px;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.3);
  box-shadow:
    0 4px 15px rgba(255, 78, 0, 0.4),
    0 0 20px rgba(236, 159, 5, 0.2);
  position: relative;
  overflow: hidden;
  animation: promo-glow 2s ease-in-out infinite;
  transition: all 0.3s ease;
}

.filter-btn.promo::before {
  content: "";
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: linear-gradient(
    45deg,
    transparent 30%,
    rgba(255, 255, 255, 0.15) 50%,
    transparent 70%
  );
  animation: promo-shine 3s ease-in-out infinite;
}

.filter-btn.promo:hover {
  transform: scale(1.08);
  box-shadow:
    0 6px 25px rgba(255, 78, 0, 0.6),
    0 0 30px rgba(236, 159, 5, 0.3);
  background: linear-gradient(135deg, #ff6b00 0%, #ffc107 100%);
}

.filter-btn.combo {
  background: linear-gradient(135deg, #28a745 0%, #20c997 100%);
  color: #ffffff;
  border: 2px solid #1e7e34;
  padding: 0.6rem 1.4rem;
  font-weight: 800;
  font-size: 0.95rem;
  letter-spacing: 0.5px;
  text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.3);
  box-shadow:
    0 4px 15px rgba(40, 167, 69, 0.4),
    0 0 20px rgba(32, 201, 151, 0.2);
  position: relative;
  overflow: hidden;
  animation: combo-glow 2s ease-in-out infinite;
  transition: all 0.3s ease;
}

.filter-btn.combo::before {
  content: "";
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: linear-gradient(
    45deg,
    transparent 30%,
    rgba(255, 255, 255, 0.15) 50%,
    transparent 70%
  );
  animation: combo-shine 3s ease-in-out infinite;
}

.filter-btn.combo:hover {
  transform: scale(1.08);
}

.combo-icon {
  font-size: 1rem;
  animation: combo-bounce 0.8s ease-in-out infinite alternate;
}

@keyframes promo-glow {
  0%,
  100% {
    box-shadow:
      0 4px 15px rgba(255, 78, 0, 0.4),
      0 0 20px rgba(236, 159, 5, 0.2);
  }
  50% {
    box-shadow:
      0 4px 20px rgba(255, 78, 0, 0.6),
      0 0 35px rgba(236, 159, 5, 0.4);
  }
}

@keyframes promo-shine {
  0% {
    transform: translateX(-100%) rotate(45deg);
  }
  100% {
    transform: translateX(100%) rotate(45deg);
  }
}

.promo-icon {
  font-size: 1rem;
  animation: promo-fire 0.8s ease-in-out infinite alternate;
}

@keyframes promo-fire {
  0% {
    transform: scale(1);
    opacity: 0.9;
  }
  100% {
    transform: scale(1.2);
    opacity: 1;
  }
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

@keyframes combo-glow {
  0%,
  100% {
    box-shadow:
      0 4px 15px rgba(40, 167, 69, 0.4),
      0 0 20px rgba(32, 201, 151, 0.2);
  }
  50% {
    box-shadow:
      0 4px 20px rgba(40, 167, 69, 0.6),
      0 0 35px rgba(32, 201, 151, 0.4);
  }
}

@keyframes combo-shine {
  0% {
    transform: translateX(-100%) rotate(45deg);
  }
  100% {
    transform: translateX(100%) rotate(45deg);
  }
}

@keyframes combo-bounce {
  0% {
    transform: scale(1);
    opacity: 0.9;
  }
  100% {
    transform: scale(1.2);
    opacity: 1;
  }
}

.filter-btn.active {
  background: #c61818;
  border-color: #c61818;
  color: white;
  box-shadow: 0 4px 15px rgba(198, 24, 24, 0.3);
}

.filter-btn.promo.active {
  background: linear-gradient(135deg, #ff6b00 0%, #ffc107 100%);
  border-color: #ff8c00;
  transform: scale(1.08);
  box-shadow:
    0 6px 25px rgba(255, 78, 0, 0.6),
    0 0 30px rgba(236, 159, 5, 0.4);
}

.filter-btn.combo.active {
  background: linear-gradient(135deg, #20c997 0%, #17a2b8 100%);
  border-color: #0d6efd;
  transform: scale(1.08);
  box-shadow:
    0 6px 25px rgba(40, 167, 69, 0.6),
    0 0 30px rgba(32, 201, 151, 0.4);
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

.summary-row.discount {
  color: #28a745;
  font-weight: 600;
  background: rgba(40, 167, 69, 0.1);
  padding: 0.5rem 0.75rem;
  border-radius: 6px;
  margin: 0.25rem 0;
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
