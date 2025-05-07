<template>
  <p
    v-bind:id="`p-${count}`"
    v-bind:style="{ color: count > 5 ? 'green' : 'red' }"
  >
    Compteur : {{ count }} <div v-html="firstName"></div>
  </p>
  <div v-if="count >= 5">Bravo, vous avez clické plus de 5x</div>
  <div v-else>Vous avez clické moins de 5x</div>
  <button @click="increment">Incrémenter</button>
  <button @click="decrement">Décrementer</button>
</template>

<script setup>
import { ref } from 'vue';

const firstName = '<span>Dylan</span>';
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
