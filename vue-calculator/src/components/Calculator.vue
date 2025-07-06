<script setup lang="ts">
defineOptions({
  name: 'CalculatorComponent'
})

import { ref } from 'vue'

const current = ref("0");
const previous = ref("");
const operator = ref<string | null>(null);
const shouldResetScreen = ref(false);

function clear() {
  current.value = "0";
  previous.value = "";
  operator.value = null;
  shouldResetScreen.value = false;
}

function sign() {
  if (current.value === "0") return;
  current.value = current.value.startsWith("-")
    ? current.value.slice(1)
    : `-${current.value}`;
}

function percent() {
  const num = parseFloat(current.value);
  current.value = (num / 100).toString();
}

function append(digit: string) {
  if (shouldResetScreen.value) {
    current.value = digit;
    shouldResetScreen.value = false;
  } else {
    if (current.value === "0" && digit !== ".") {
      current.value = digit;
    } else {
      current.value += digit;
    }
  }
}

function dot() {
  if (shouldResetScreen.value) {
    current.value = "0.";
    shouldResetScreen.value = false;
  } else if (!current.value.includes('.')) {
    current.value += '.';
  }
}

function setOperator(op: string) {
  if (operator.value && !shouldResetScreen.value) {
    calculate();
  }
  previous.value = current.value;
  operator.value = op;
  shouldResetScreen.value = true;
}

function calculate() {
  if (!operator.value || shouldResetScreen.value) return;

  const prev = parseFloat(previous.value);
  const curr = parseFloat(current.value);
  let result = 0;

  switch (operator.value) {
    case '+':
      result = prev + curr;
      break;
    case '-':
      result = prev - curr;
      break;
    case '×':
      result = prev * curr;
      break;
    case '÷':
      if (curr === 0) {
        current.value = 'Error';
        return;
      }
      result = prev / curr;
      break;
  }

  current.value = result.toString();
  operator.value = null;
  shouldResetScreen.value = true;
}

function divide() {
  setOperator('÷');
}

function times() {
  setOperator('×');
}

function minus() {
  setOperator('-');
}

function add() {
  setOperator('+');
}
</script>

<template>
  <div class="calculator">
    <div class="display">{{ current }}</div>
    <div @click="clear" class="btn">C</div>
    <div @click="sign" class="btn">+/-</div>
    <div @click="percent" class="btn">%</div>
    <div @click="divide" class="btn operator">÷</div>
    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div @click="times" class="btn operator">×</div>
    <div @click="append('4')" class="btn">4</div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="minus" class="btn operator">-</div>
    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="add" class="btn operator">+</div>
    <div @click="append('0')" class="btn zero">0</div>
    <div @click="dot" class="btn">.</div>
    <div @click="calculate" class="btn operator">=</div>
  </div>
</template>

<style scoped>
.calculator {
  text-align: center;
  margin: 0 auto;
  width: 400px;
  font-size: 40px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}

.display {
  grid-column: 1 / 5;
  background-color: #333;
  color: white;
}

.zero {
  grid-column: 1 / 3;
}

.btn {
  background-color: #f2f2f2;
  border: 1px solid #999;
}

.operator {
  background-color: orange;
  color: white;
}

</style>
