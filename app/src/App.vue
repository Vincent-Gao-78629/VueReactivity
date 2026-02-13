<template>
  <h1>Calculator</h1>
  <div>
    <button v-for="number in numbers">{{ number }}</button>
    <button>+</button>
    <button>-</button>
    <button>x</button>
    <button>/</button>
  </div>
</template>

<script setup>
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
let number1
let number2
const history = []
</script>

<style scoped></style>
