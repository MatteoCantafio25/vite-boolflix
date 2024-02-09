<script>
import ProductionCard from './ProductionCard.vue';
import { store } from '../data/store.js';
export default {
    name: "ProductionList",
    data: () => ({
        store,
    }),
    components: {
        ProductionCard,
    }
};
</script>

<template>
    <div class="production-base">
        <h4 v-if="store.movies.length">MOVIES</h4>
        <div class="row row-cols-4">
            <div class="col" v-for="movie in store.movies" :key="movie.id">
                <ProductionCard :production="movie" />
            </div>
        </div>
        <h4 v-if="store.series.length">SERIES</h4>
        <div class="row row-cols-4">
            <div class="col" v-for="serie in store.series" :key="serie.id">
                <ProductionCard :production="serie" />
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped >
.production-base {
    max-width: 1450px;
    margin: 0 auto;

    h4 {
        color: white;
    }
}

.border-white {
    border: 2px dashed white;
}
</style>