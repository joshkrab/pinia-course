<template>
  <main>
    <header class="header">
      <img src="/logo.svg" alt="logo" class="header-logo" />
      <h2>My Favorite Movies</h2>
    </header>

    <div class="tabs">
      <button :class="['btn', { btn_green: movieStore.activeTab === 1 }]">
        Favorite
      </button>
      <button :class="['btn', { btn_green: movieStore.activeTab === 2 }]">
        Search
      </button>
    </div>

    <div class="movies" v-if="movieStore.activeTab === 1">
      <h3>All movies</h3>
      <Movie
        v-for="movie of movieStore.movies"
        :key="movie.id"
        :movie="movie"
      />
    </div>
    <div class="search" v-if="movieStore.activeTab === 2">Search</div>
  </main>
</template>

<script setup>
import { useMovieStore } from "./stores/MovieStore";
import Movie from "./components/Movie.vue";
const movieStore = useMovieStore();
</script>

<style lang="css">
.header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
}
.header-logo {
  max-width: 50px;
  margin-right: 10px;
}
.btn {
  border: none;
  width: 100px;
  height: 40px;
  font-size: 14px;
  margin: 0 10px;
  border-radius: 10px;
  cursor: pointer;
  background: #efefef;
}
.btn:hover {
  opacity: 0.7;
}
.btn_green {
  background: #37df5c;
}

.tabs {
  display: flex;
  justify-content: center;
  margin-bottom: 30px;
}
</style>
