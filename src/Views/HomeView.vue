<script setup>
import { ref, computed, onMounted } from "vue";

import PizzaList from "../components/PizzaList.vue";
import SizeSelector from "../components/SizeSelector.vue";
import ToppingSelector from "../components/ToppingSelector.vue";
import TotalPrice from "../components/TotalPrice.vue";

import pizzasData from "../assets/json/pizza-list.json";
import sizesData from "../assets/json/size-list.json";
import toppingsData from "../assets/json/topping-list.json";
import Navbar from "../components/Navbar.vue";
import Footer from "../components/Footer.vue";

// Buat reactive state
const pizzas = ref(pizzasData.data);
const sizes = ref(sizesData.data);
const toppings = ref(toppingsData.data);
const selectedPizza = ref(null);
const selectedSize = ref(null);
const selectedToppings = ref([]);

// Fungsi memilih pizza
const selectPizza = (pizza) => {
  selectedPizza.value = pizza;
  selectedSize.value = sizes.value.find(size => size.name === "Small") || null; // Pilih ukuran Small
  selectedToppings.value = []; // Reset topping saat pilih pizza baru
};

// Perhitungan total harga
const totalPrice = computed(() => {
  if (!selectedPizza.value) return 0;

  let price = selectedPizza.value.discount?.is_active
    ? selectedPizza.value.discount.final_price
    : selectedPizza.value.price;

  // Tambahkan harga ukuran jika ada
  if (selectedSize.value) {
    price += selectedSize.value.extra_price;
  }

  // Tambahkan harga untuk topping tambahan
  selectedToppings.value.forEach((toppingId) => {
    const topping = toppings.value.find(t => t.id === toppingId);
    if (topping && !selectedPizza.value.toppings.some(t => String(t.id) === String(topping.id))) {
      price += topping.price;
    }
  });

  return price.toFixed(2);
});

// Pilih default pizza dan size saat aplikasi dijalankan
onMounted(() => {
  selectedPizza.value = pizzas.value.find(pizza => pizza.name === "Cheese Pizza") || pizzas.value[0];
  selectedSize.value = sizes.value.find(size => size.name === "Small") || sizes.value[0];
});
</script>

<template>
  <div>

    <Navbar />
    <img src="../assets/img/hero.png" alt="Hero Image" class="w-full">
    <div class="container mx-auto flex flex-col md:flex-row justify-between items-center">
      <div class="space-y-20">
        <PizzaList :pizzas="pizzas" v-model:selectedPizza="selectedPizza" />
        <div>
          <SizeSelector :sizes="sizes" v-model="selectedSize" />
          <ToppingSelector :toppings="toppings" v-model="selectedToppings" :selectedPizza="selectedPizza" />
        </div>
      </div>
      
      <div>
        <TotalPrice :totalPrice="totalPrice" :selectedPizza="selectedPizza" :selectedSize="selectedSize" :selectedToppings="selectedToppings"/>
      </div>
    </div>
    <Footer />
    
  </div>
</template>
