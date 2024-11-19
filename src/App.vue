<script setup>
import { reactive } from 'vue';
import Header from './components/Header.vue'
import Digits from './components/Digits.vue'

const estado = reactive({
  numTemp1: '0',
  numTemp2: '0',
  operations: '+',
})

const sum = () => {
  
}

</script>

<template>
  <div class="container">
    <Header/>
    <Digits/>
  </div>
</template>

<style scoped>

</style>