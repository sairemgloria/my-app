<script setup>
import { ref, computed } from "vue";

const animes = ref([
  {
    id: 1,
    title: "Naruto",
    genre: ["Action", "Fantasy", "Comedy"],
    author: "Naruto Uzumaki",
    createdAt: "01/01/2001",
  },
  {
    id: 2,
    title: "Bleach",
    genre: ["Fantasy", "Adventure", "Supernatural"],
    author: "Japan",
    createdAt: "02/02/2002",
  },
]);

// computed property to sort the genres alphabetically for each anime
const sortedGenres = computed(() => {
  // sort genres for each anime
  return animes.value.map((anime) => {
    return {
      ...anime, // copy the anime object
      genre: [...anime.genre].sort(), // sort genres of each anime
    };
  });
});
</script>

<template>
  <div class="wrapper">
    <div v-for="anime in sortedGenres" :key="anime.id">
      <div class="card w-96 bg-base-200 card-lg shadow-sm m-4">
        <div class="card-body">
          <h1 class="card-title text-3xl">{{ anime.title }}</h1>
          <div class="flex gap-1">
            <div
              v-for="(genre, index) in anime.genre"
              :key="index"
              class="badge badge-primary"
            >
              {{ genre }}
            </div>
          </div>
          <p>Author: {{ anime.author }}</p>
          <small>Released Date: {{ anime.createdAt }}</small>
          <div class="justify-end card-actions">
            <button class="btn btn-outline btn-error">
              <span class="material-icons">delete</span>
            </button>

            <button class="btn btn-outline btn-success">
              <span class="material-icons">bookmark_border</span>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>