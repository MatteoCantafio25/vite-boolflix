<script>
import ProductionList from './movies/ProductionList.vue';
export default {
    name: "AppMain",
    components: {
        ProductionList,
    }
};
</script>

<template>
    <main class="pt-5">
        <ProductionList />
    </main>
</template>

<style lang="scss" scoped >
main {
    background-color: #434343;
    min-height: 90vh;
}
</style>