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
    },

    computed: {
        arrayLenght() {
            return store.movies.length || store.series.length
        }
    }
};
</script>

<template>
    <div v-if="arrayLenght" class="production-base mt-5">
        <h4 v-if="store.movies.length">MOVIES</h4>
        <div class="row row-cols-4 mb-5">
            <div class="col g-4" v-for="movie in store.movies" :key="movie.id">
                <ProductionCard :production="movie" />
            </div>
        </div>
        <h4 v-if="store.series.length">SERIES</h4>
        <div class="row row-cols-4 pb-5">
            <div class="col g-4" v-for="serie in store.series" :key="serie.id">
                <ProductionCard :production="serie" />
            </div>
        </div>
    </div>
    <div v-else class="no-content-yet d-flex align-items-center justify-content-center">
        <div class="title d-flex align-items-center justify-content-center">
            <h1>Cerca in alto a destra per esplorare <br> un mondo mai visto</h1>
        </div>
    </div>
</template>

<style lang="scss" scoped >
.production-base {
    max-width: 1550px;
    margin: 0 auto;

    h4 {
        color: white;
        font-size: 2.5rem;
    }
}

.no-content-yet {
    height: 700px;
    width: 1550px;
    margin: 0 auto;
    background-image: url(../../assets/img/boolfix-background.png);
    background-size: cover;
    background-repeat: no-repeat;
}


.title {
    width: 60%;
    height: 160px;
    background-color: rgba(0, 0, 0, 0.5);
    border-radius: 7px;
    text-align: center;

    h1 {
        color: white;
        font-size: 3rem;
        font-weight: bold;
        margin-bottom: 0;
        line-height: 80px;
    }
}
</style>