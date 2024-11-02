<template>
  <div>
    <pre>{{ data }}</pre>
  </div>
</template>

<script setup lang="ts">
const route = useRoute();

const { data } = await useFetch(
  `http://www.omdbapi.com/?apikey=e0207309&i=${route.params.id}`,
  {
    pick: ["Plot", "Title", "Error"],
    key: `/movies/${route.params.id}`,
  }
);

if (data.value.Error === "Incorrect IMDb ID.") {
  showError({ statusCode: 404, statusMessage: "Page not found" });
}
</script>

<style scoped></style>
