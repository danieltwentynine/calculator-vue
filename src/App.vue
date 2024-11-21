<script setup>
import { reactive, computed } from 'vue';
import Header from './components/Header.vue';
import Digits from './components/Digits.vue';

const estado = reactive({
  numTemp1: 0,
  numTemp2: 0,
  operations: '+',
});

// Computed property for the result
const result = computed(() => {
  const { numTemp1, numTemp2, operations } = estado;

  switch (operations) {
    case '-':
      return numTemp1 - numTemp2;
    case '*':
      return numTemp1 * numTemp2;
    case '/':
      return numTemp2 !== 0 ? numTemp1 / numTemp2 : 'Error: Division by zero';
    default: // Default to addition
      return numTemp1 + numTemp2;
  }
});
</script>

<template>
  <div class="container">
    <Header />
    <Digits :num1="estado.numTemp1" :get-num1="evento => (estado.numTemp1 = Number(evento.target.value))"
      :num2="estado.numTemp2" :get-num2="evento => (estado.numTemp2 = Number(evento.target.value))"
      :get-operation="evento => (estado.operations = evento.target.value)" :answer="result" />
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