<template>
  <p>Compteur : {{ count }}</p>
  <button @click="increment">Incrémenter</button>
  <button @click="decrement">Décrementer</button>
</template>

<script setup>
import { ref } from 'vue';

const count = ref(0);
console.log(count, count.value);
const increment = (e) => {
  count.value++;
};

const decrement = (e) => {
  count.value--;
};
</script>

<style></style>
