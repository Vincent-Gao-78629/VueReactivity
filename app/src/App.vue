<template>
  <h1>Calculator</h1>
  <div id="calcButtons">
    <button v-for="number in numbers" :key="number" @click="selectNumber(number)">
      {{ number }}
    </button>
    <button @click="calculate">=</button>
    <!-- make calc stop selection -->

    <button @click="selectOperator('+')">+</button>
    <button @click="selectOperator('-')">-</button>
    <button @click="selectOperator('*')">*</button>
    <button @click="selectOperator('/')">/</button>
    <button @click="removeLast">CE</button>
    <!-- bad -->
    <button @click="negate">(−)</button>
    <!-- bad -->

    <button @click="clear">C</button>
  </div>

  <div>{{ number1 }} {{ operator }} {{ number2 }} = {{ result }}</div>
</template>

<script setup>
import { ref } from 'vue'

const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
const input = ref('')
const number1 = ref(null)
const number2 = ref(null)
const operator = ref(null)
const result = ref(null)

function selectNumber(number) {
  if (operator.value === null) {
    input.value += number
    number1.value = Number(input.value)
  } else {
    input.value += number
    number2.value = Number(input.value)
  }
}
function selectOperator(op) {
  if (number1.value != null || number2.value === null) {
    // make so if have nnumber2, op cant be seelc, after calc, n2 cant seelct
    operator.value = opt
    input.value = ''
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
  if (number2.value != 0) {
    result.value = number1.value / number2.value
  } else {
    result.value = 'Error: Division by zero'
  }
}
function removeLast(number1, number2) {}

function negate(number1, number2) {
  if (operator.value === null) {
    input.value += number
    number1.value = -1 * Number(input.value)
  } else {
    input.value += number
    number2.value = -1 * Number(input.value)
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
  input.value = ''
  number1.value = null
  number2.value = null
  operator.value = null
  result.value = null
}
</script>

<style scoped>
#calcButtons {
  flex: auto;
  max-width: 15%;
}

button {
  margin: 2px;
  height: 50px;
  width: 50px;
  padding: 1px;
  font-size: 18px;
}
</style>
