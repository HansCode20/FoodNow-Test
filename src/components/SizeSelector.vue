<template>
  <div>
    <h2 class="text-lg font-semibold mb-3">Select Size:</h2>
    <div class="flex items-center gap-5">
      <div v-for="size in sizes" :key="size.id" class="flex items-center gap-2">
        <input
          type="radio"
          :id="'size-' + size.id"
          :value="size"
          v-model="selectedSize"
          class="cursor-pointer"
        />
        <label :for="'size-' + size.id" class="cursor-pointer">{{ size.name }} (+${{ size.extra_price }})</label>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits, computed } from "vue";

const props = defineProps(["sizes", "modelValue"]);
const emit = defineEmits(["update:modelValue"]);

const selectedSize = computed({
  get: () => props.modelValue,
  set: (size) => emit("update:modelValue", size),
});
</script>

<style scoped>
input[type="radio"] {
  appearance: none;
  width: 20px;
  height: 20px;
  border: 1px solid gray;
  border-radius: 50%;
  cursor: pointer;
}

input[type="radio"]:checked {
background-color: #ffffff; /* Warna oranye saat checked */
border: 1px solid #e77e23; /* Border tetap oranye */
box-shadow: 0 0 5px rgba(231, 126, 35, 0.5); /* Efek glow (opsional) */
}

input[type="radio"]:checked::before {
content: "";
width: 10px;
height: 10px;
background-color:  #e77e23; /* Warna putih di tengah */
border-radius: 50%;
display: block;
position: relative;
top: 50%;
left: 50%;
transform: translate(-50%, -50%);
}

</style>
