<script>
import MovieCard from './MovieCard.vue';
import { store } from '../data/store.js';
import { imgBaseEndpoint } from '../data/index.js';
export default {
    name: "MoviesList",
    data: () => ({
        store,
        imgBaseEndpoint,
    }),
    components: {
        MovieCard,
    }
};
</script>

<template>
    <div class="movies-base">
        <div class="row row-cols-4">
            <div class="col" v-for="movie in store.movies" :key="movie.id">
                <MovieCard :image="`${imgBaseEndpoint}${movie.poster_path}`" :title="movie.title"
                    :original="movie.original_title" :lang="movie.original_language" :vote="movie.vote_average" />
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped >
.movies-base {
    max-width: 1400px;
    margin: 0 auto;
    border: 2px dashed white;
}
</style>