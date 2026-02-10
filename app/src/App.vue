<template>
  <h1>PokeBowl Builder</h1>

  <button @click="console.log(bowl) .disable">iuergvgeuv</button>
</template>

<script setup>
import { ref, reactive } from 'vue'
function addToBowl() {}
let bowl = ref({
  base: ['white rice'],
  ingredients: ['cucumber', 'edamame', 'mango', 'seaweed salad', 'avocado'],
  protein: ['salmon', 'salmon'],
  toppings: ['crispy onions'],
  sauces: ['spicy mayo', 'eel sauce'],
})
const items = {
  base: ['white rice', 'brown rice', 'salad'],
  ingredients: ['cucumber', 'edamame', 'mango', 'seaweed salad', 'avocado'],
  protein: ['salmon', 'tuna', 'tofu', 'shrimp', 'chicken'],
  toppings: ['sesame seeds', 'green onions', 'seaweed', 'crispy onions', 'fried garlic'],
  sauces: ['soy sauce', 'spicy mayo', 'ponzu', 'eel sauce', 'wasabi mayo'],
}
</script>

<style scoped></style>
