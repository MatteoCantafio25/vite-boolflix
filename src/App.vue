<script>
import axios from 'axios';
import { store } from '@/components/data/store.js';
import { apiKey, endpointMovie, endpointSeries } from './components/data/index.js';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';

export default {
  name: "Vite Boolflix",
  components: {
    AppHeader,
    AppMain,
    FontAwesomeIcon
  },

  methods: {
    fetchMovies(term) {
      const endpoint = `${endpointMovie}?api_key=${apiKey}&query=${term}&language=it-IT`;
      axios.get(endpoint).then(res => {
        store.movies = res.data.results;
      })
    },

    fetchSeries(term) {
      const endpoint = `${endpointSeries}?api_key=${apiKey}&query=${term}&language=it-IT`;
      axios.get(endpoint).then(res => {
        store.series = res.data.results;
      })
    },

    searchProduction(term) {
      console.log("devo cercare...", term);
      this.fetchMovies(term);
      this.fetchSeries(term);
    },
  }
}
</script>

<template>
  <AppHeader @search-production="searchProduction" />
  <AppMain />
</template>

<style lang="scss">
/* Style here */
</style>