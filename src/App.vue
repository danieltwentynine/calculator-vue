<script setup>
import { reactive } from 'vue';
import Header from './components/Header.vue';
import Digits from './components/Digits.vue';

const estado = reactive({
  numTemp1: 0,
  numTemp2: 0,
  operations: '+',
  result: null, // Holds the result of the calculation
});

const sum = () => estado.numTemp1 + estado.numTemp2;
const sub = () => estado.numTemp1 - estado.numTemp2;
const multi = () => estado.numTemp1 * estado.numTemp2;
const divi = () => (estado.numTemp2 !== 0 ? estado.numTemp1 / estado.numTemp2 : 'Error: Division by zero');

const answer = () => {
  const { operations } = estado;

  switch (operations) {
    case '-':
      return sub();
    case '*':
      return multi();
    case '/':
      return divi();
    default:
      return sum();
  }
};

const showAnswer = () => {
  estado.result = answer(); // Calculate and store the result in estado.result
};
</script>

<template>
  <div class="container">
    <Header />
    <Digits
      :num1="estado.numTemp1"
      :get-num1="evento => (estado.numTemp1 = Number(evento.target.value))"
      :num2="estado.numTemp2"
      :get-num2="evento => (estado.numTemp2 = Number(evento.target.value))"
      :get-operation="evento => (estado.operations = evento.target.value)"
      :answer="estado.result"
      :calculate="showAnswer"
    />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}
</style>