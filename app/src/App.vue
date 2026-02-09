<template>
  <h1>PokeBowl Builder</h1>
  <button @click="bowl.push('salmon')">Add Salmon</button>
  <p>Your bowl contains: {{ bowl.join(', ') }}</p>
</template>

<script setup>
import { ref } from 'vue'
let bowl = ref([])
const base = ['white rice', 'brown rice', 'salad']
const ingredients = ['cucumber', 'edamame', 'carrots', 'seaweed salad', 'avocado']
const protein = ['salmon', 'tuna', 'tofu', 'shrimp', 'chicken']
const toppings = ['sesame seeds', 'green onions', 'seaweed']
const sauces = ['soy sauce', 'spicy mayo', 'ponzu', 'eel sauce']
</script>

<style scoped></style>
