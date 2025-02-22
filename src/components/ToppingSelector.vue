<template>
  <div class="mt-10">
    <h3 class="font-bold text-2xl mb-5">Toppings</h3>
    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-5 max-w-4xl mt-5">
      <label
        v-for="topping in toppings"
        :key="topping.id"
        class="font-bold text-sm p-4 rounded-full transition duration-200 text-center cursor-pointer border border-gray-300"
        :class="{
          'bg-orange-200 border-orange-500 text-orange-400': selectedToppings.includes(topping.id), // Jika topping dipilih
          'bg-white text-black hover:bg-orange-200 ': !selectedToppings.includes(topping.id), // Jika tidak dipilih
          'cursor-not-allowed hover:bg-white text-gray-400 border-gray-300': (selectedPizza?.toppings || []).map(String).includes(String(topping.id)) // Topping bawaan (disabled)
        }"
      >
        <input
          type="checkbox"
          :value="topping.id"
          :checked="selectedToppings.includes(topping.id)"
          :disabled="(selectedPizza?.toppings || []).map(String).includes(String(topping.id))"
          @change="toggleTopping(topping.id)"
          class="hidden"
        />
        {{ topping.name }}
      </label>
    </div>
  </div>
</template>

<script setup>
import { defineProps, computed } from "vue";

const props = defineProps({
  toppings: Array,
  modelValue: Array,
  selectedPizza: Object,
});

const emit = defineEmits(["update:modelValue"]);

const selectedToppings = computed(() => props.modelValue ?? []);

const toggleTopping = (id) => {
  if ((props.selectedPizza?.toppings || []).map(String).includes(String(id))) return; // Skip topping bawaan

  let updatedToppings = [...selectedToppings.value]; // Buat salinan array agar Vue melacak perubahan
  if (updatedToppings.includes(id)) {
    updatedToppings = updatedToppings.filter((toppingId) => toppingId !== id); // Hapus jika sudah dipilih
  } else {
    updatedToppings.push(id); // Tambah jika belum dipilih
  }

  emit("update:modelValue", updatedToppings); // Emit perubahan ke parent
};
</script>

<style scoped>
/* Tambahkan gaya agar label tetap terlihat seperti tombol */
label {
  display: flex;
  align-items: center;
  justify-content: center;
  min-width: 80px;
  user-select: none;
}
</style>
