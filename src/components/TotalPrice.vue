<template>
  <div class="mt-40 w-80  p-6 rounded-lg shadow-lg bg-white">
      <h1 class="text-2xl font-bold mb-4 text-[#e77e23]">Payment Summary</h1>

      <div v-if="selectedPizza" class="flex justify-between items-center mb-4">
        <p class="text-gray-700">{{ selectedPizza.name }}</p>
        <p>${{ selectedPizza.price }}</p>
      </div>

      <div v-if="selectedSize" class="flex justify-between items-center mb-4">
        <p class="text-gray-700">Size - {{ selectedSize.name }}</p>
        <p>${{ selectedSize.extra_price }}</p>
      </div>

      <div v-if="selectedToppings.length > 0">
      <ul class="ext-gray-700">
      <li v-for="toppingId in selectedToppings" :key="toppingId" class="flex justify-between items-center mb-4">
        {{ getToppingName(toppingId) }}
        <span class="font-medium">${{ toppingsData.data.find(t => t.id === toppingId).price }}</span>
      </li>
    </ul>
  </div>
    <h2 class="flex justify-between items-center text-xl font-medium mt-8">Total Price:
      <span class="font-medium text-[#e77e23]">${{ totalPrice }}</span>
    </h2>

    <button class="mt-4 w-full bg-[#e77e23] text-white py-2 rounded-full">Order Now</button>
  </div>
</template>

<script setup>
import { defineProps } from "vue";
import toppingsData from "../assets/json/topping-list.json"; // Import daftar topping

const props = defineProps(["totalPrice", "selectedPizza", "selectedSize", "selectedToppings"]);

// Fungsi mencari nama topping berdasarkan ID
const getToppingName = (id) => {
  const topping = toppingsData.data.find(t => t.id === id);
  return topping ? topping.name : "Unknown Topping";
};
</script>

