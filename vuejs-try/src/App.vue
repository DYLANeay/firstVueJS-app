<template>
  <p :style="{ color: count > 5 ? 'green' : 'red' }">
    Compteur : {{ count }} {{ firstName }}
  </p>

  <div v-if="count >= 5">Bravo, vous avez clické plus de 5x</div>
  <div v-else>Vous avez clické moins de 5x</div>
  <button @click="increment">Incrémenter</button>
  <button @click="decrement">Décrementer</button>
  <hr />
  <button @click="sortMovies">Réorganiser</button>

  <!-- Prevent default form submission, which is useful because form submission auto reload the page otherwise -->
  <form action="" @submit.prevent="addMovie">
    <input type="text" placeholder="New Movie" v-model="movieName" />
    <button>Add</button>
  </form>

  <ul>
    <li :key="movie.title" v-for="movie in movies">
      {{ movie.title }} {{ ' : ' + movie.year }}
      <button @click="deleteMovie(movie)">Supprimer</button>
    </li>
  </ul>
</template>

<script setup>
import { ref } from 'vue';

// Data
const count = ref(0);
const movieName = ref('');
const movies = ref([
  { title: 'Star Wars', year: 1977 },
  { title: 'The Empire Strikes Back', year: 1980 },
  { title: 'Return of the Jedi', year: 1983 },
]);
const firstName = ref('Dylan');

// Functions
const increment = () => count.value++;
const decrement = () => count.value--;
const deleteMovie = (movie) => {
  movies.value = movies.value.filter((m) => m !== movie);
};
const sortMovies = () => {
  movies.value.sort((a, b) => {
    if (a.title < b.title) return -1;
    if (a.title > b.title) return 1;
    return 0;
  });
};
const addMovie = () => {
  movies.value.push({
    title: movieName.value,
    year: new Date().getFullYear(),
  });
  movieName.value = '';
};
</script>

<style></style>
