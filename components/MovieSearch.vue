<template>
  <div>
    <form @submit.prevent="search">
      <input type="text" v-model="query" />
      <button>Search</button>
    </form>
    <ul style="display: flex; flex-wrap: wrap; gap: 10px; list-style: none">
      <li v-for="movie in movies" :key="movie.imdbID">
        <NuxtLink :to="{ name: 'movies-id', params: { id: movie.imdbID } }">
          <NuxtImg
            :src="movie.Poster"
            :alt="movie.title"
            width="300"
            height="200"
            loading="lazy"
          />
        </NuxtLink>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
const movies = ref([]);
const query = ref("spiderman");

async function search() {
  const { Search } = await $fetch(
    `https://www.omdbapi.com/?apikey=e0207309&s=${query.value}`
  );
  movies.value = Search;
}

search();
</script>

<style scoped></style>
