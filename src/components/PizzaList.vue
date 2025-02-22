<template>
  <div class="px-4 md:px-0">
    <h2 class="mt-20 mb-10 font-bold text-2xl sm:text-3xl md:text-4xl text-[#e77e23]">
      Choose your pizza
    </h2>
    
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6 max-w-6xl mx-auto">
      <label 
        v-for="pizza in pizzas" 
        :key="pizza.id" 
        class="relative group flex items-center gap-4 sm:gap-5 p-4 sm:px-6 sm:py-5 rounded-lg cursor-pointer transition duration-200 border border-gray-200"
        :class="selectedPizza?.id === pizza.id 
          ? 'bg-[#e77e23] text-white scale-105 shadow-lg' 
          : 'bg-white text-black hover:bg-orange-200'"
      >
        <!-- Input radio -->
        <input 
          type="radio" 
          :value="pizza" 
          :checked="selectedPizza?.id === pizza.id"
          @change="$emit('update:selectedPizza', pizza)" 
          class="hidden"
        />

        <!-- Ribbon Diskon -->
        <img 
          v-if="pizza.discount.is_active" 
          src="../assets/img/ribbon.svg" 
          alt="Discount Ribbon" 
          class="absolute top-0 right-0 w-16 sm:w-20"
        />

        <!-- Gambar Pizza -->
        <div class="w-16 sm:w-24 md:w-28">
          <img 
            :src="pizza.images" 
            :alt="pizza.name" 
            class="w-full group-hover:rotate-12 transition duration-200"
          />
        </div>

        <!-- Nama & Harga -->
        <div>
          <h3 class="font-bold text-lg sm:text-xl whitespace-nowrap">{{ pizza.name }}</h3>
          <p class="font-medium text-sm sm:text-base">
            ${{ pizza.discount.is_active ? pizza.discount.final_price : pizza.price }}
            <span 
              v-if="pizza.discount.is_active" 
              :class="[
                'line-through font-medium ml-2', 
                selectedPizza?.id === pizza.id ? 'text-white' : 'text-gray-500'
              ]">
              ${{ pizza.price }}
            </span>
          </p>
        </div>
      </label>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

defineProps({
  pizzas: Array,
  selectedPizza: Object,
});

const emit = defineEmits(["update:selectedPizza"]);
</script>
