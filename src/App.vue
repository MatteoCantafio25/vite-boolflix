<script>
import axios from 'axios';
import { store } from '@/components/data/store.js';
import { apiKey } from './components/data/index.js';
import { endpointMovie } from './components/data/index.js';
import { endpointSeries } from './components/data/index.js';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';

export default {
  name: "Vite Boolflix",
  components: {
    AppHeader,
    AppMain,
  },

  methods: {
    fetchMovies(endpointMovie) {
      axios.get(endpointMovie).then(res => {
        store.movies = res.data.results;
      })
    },

    fetchSeries(endpointSeries) {
      axios.get(endpointSeries).then(res => {
        store.series = res.data.results;
      })
    },

    searchProduction(term) {
      console.log("devo cercare...", term);
      const searchEndpointMovie = `${endpointMovie}?api_key=${apiKey}&query=${term}&language=it-IT`;
      this.fetchMovies(searchEndpointMovie);

      const searchEndpointSeries = `${endpointSeries}?api_key=${apiKey}&query=${term}&language=it-IT`;
      this.fetchSeries(searchEndpointSeries);

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