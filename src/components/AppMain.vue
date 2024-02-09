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
    <main>
        <ProductionList />
    </main>
</template>

<style lang="scss" scoped >
main {
    background-color: #1B1B1B;
    min-height: 90vh;
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>