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
        <h4>MOVIES</h4>
        <div class="row row-cols-4 border-white">
            <div class="col" v-for="movie in store.movies" :key="movie.id">
                <ProductionCard :production="movie" />
            </div>
        </div>
        <h4>SERIES</h4>
        <div class="row row-cols-4 border-white">
            <div class="col" v-for="serie in store.series" :key="serie.id">
                <ProductionCard :production="serie" />
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped >
.production-base {
    max-width: 1400px;
    margin: 0 auto;

    h4 {
        color: white;
    }
}

.border-white {
    border: 2px dashed white;
}
</style>