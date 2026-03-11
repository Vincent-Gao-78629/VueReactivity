<template>
  <h1>Calculator</h1>
  <div id="calcButtons">
    <button v-for="number in numbers" :key="number" @click="selectNumber(number)">
      {{ number }}
    </button>

    <button @click="selectOperator('+')">+</button>
    <button @click="selectOperator('-')">-</button>
    <button @click="selectOperator('*')">*</button>
    <button @click="selectOperator('/')">/</button>

    <button @click="negate">±</button>
    <button @click="removeLast">CE</button>
    <button @click="clear">C</button>
    <button @click="calculate">=</button>
  </div>

  <div>{{ equation }}</div>

  <div>
    <h2>History</h2>
    <li v-for="(calc, index) in history" :key="index">{{ calc }}</li>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
const input = ref('')
const number1 = ref(null)
const number2 = ref(null)
const operator = ref(null)
const result = ref(null)

const history = ref([])

const equation = computed(() => {
  if (result.value !== null) {
    return `${number1.value ?? ''} ${operator.value ?? ''} ${number2.value ?? ''} = ${result.value}`
  }
  return `${number1.value ?? ''} ${operator.value ?? ''} ${input.value ?? ''}`
})

function selectNumber(number) {
  input.value += number
}

function selectOperator(op) {
  if (operator.value === null && input.value !== '') {
    number1.value = Number(input.value)
    operator.value = op
    input.value = ''
  } else if (result.value !== null) {
    number1.value = result.value
    operator.value = op
    input.value = ''
    result.value = null
  }
}

function calculate() {
  if (operator.value && input.value !== '') {
    number2.value = Number(input.value)

    if (operator.value === '+') {
      result.value = number1.value + number2.value
    } else if (operator.value === '-') {
      result.value = number1.value - number2.value
    } else if (operator.value === '*') {
      result.value = number1.value * number2.value
    } else if (operator.value === '/') {
      if (number2.value != 0) {
        result.value = number1.value / number2.value
      } else {
        result.value = 'Error: Division by zero'
      }
    }
    history.value.unshift(`${number1.value} ${operator.value} ${number2.value} = ${result.value}`)

    input.value = ''
  }
}
function removeLast() {
  input.value = input.value.slice(0, -1)
}

function negate() {
  if (input.value !== '') {
    if (input.value.startsWith('-')) {
      input.value = input.value.slice(1)
    } else {
      input.value = '-' + input.value
    }
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
  display: grid;
  grid-template-columns: repeat(3, 50px);
  gap: 5px;
  margin-top: 10px;
}

button {
  height: 50px;
  font-size: 18px;
  cursor: pointer;
}

div {
  margin-top: 20px;
  font-size: 24px;
}
</style>
