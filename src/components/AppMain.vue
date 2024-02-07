<script>
import MoviesList from './movies/MoviesList.vue';
export default {
    name: "AppMain",
    components: {
        MoviesList,
    }
};
</script>

<template>
    <main class="pt-5">
        <MoviesList />
    </main>
</template>

<style lang="scss" scoped >
main {
    background-color: #434343;
    min-height: 90vh;
}
</style>