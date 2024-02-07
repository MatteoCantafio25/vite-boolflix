<script>
import axios from 'axios';
import { store } from '@/components/data/store.js';
import { apiKey } from './components/data/index.js';
import { endpoint } from './components/data/index.js';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
export default {
  name: "Vite Boolflix",
  components: {
    AppHeader,
    AppMain,
  },

  methods: {
    fetchMovies(endpoint) {
      axios.get(endpoint).then(res => {
        store.movies = res.data.results;
      })
    },
    searchMovies(term) {
      console.log("devo cercare...", term);
      const searchEndpointMovie = `${endpoint}?api_key=${apiKey}&query=${term}&language=it-IT`;
      this.fetchMovies(searchEndpointMovie);
      console.log(searchEndpointMovie);
    }
  },

};
</script>

<template>
  <AppHeader @search-movies="searchMovies" />
  <AppMain />
</template>

<style lang="scss">
/* Style here */
</style>