<template>
  <h1>Calculator</h1>
  <button v-for="number in numbers" :key="number" @click="selectNumber(number)">
    {{ number }}
  </button>
  <button @click="selectOperator('+')">+</button>
  <button @click="selectOperator('-')">-</button>
  <button @click="selectOperator('*')">*</button>
  <button @click="selectOperator('/')">/</button>
  <button @click="calculate">=</button>
  <button @click="clear">Clear</button>
  <div>{{ number1 }} {{ operator }} {{ number2 }} = {{ result }}</div>
</template>

<script setup>
import { ref } from 'vue'

const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
const number1 = ref(null)
const number2 = ref(null)
const operator = ref(null)
const result = ref(null)

function selectNumber(number) {
  if (operator.value === null) {
    number1.value = number
  } else {
    number2.value = number
  }
}
function selectOperator(op) {
  if (number1.value != null) {
    operator.value = op
  }
}
function add() {
  result.value = number1.value + number2.value
}
function subtract() {
  result.value = number1.value - number2.value
}
function multiply() {
  result.value = number1.value * number2.value
}
function divide() {
  if (number2.value !== 0) {
    result.value = number1.value / number2.value
  } else {
    result.value = 'Error: Division by zero'
  }
}

function calculate() {
  if (operator.value === '+') {
    add()
  } else if (operator.value === '-') {
    subtract()
  } else if (operator.value === '*') {
    multiply()
  } else if (operator.value === '/') {
    divide()
  }
}
function clear() {
  number1.value = null
  number2.value = null
  operator.value = null
  result.value = null
}
</script>

<style scoped>
button {
  margin: 2px;
  padding: 10px;
  font-size: 18px;
}
</style>
