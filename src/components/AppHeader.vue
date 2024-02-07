<script>
import SearchForm from './SearchForm.vue';
export default {
    name: "AppHeader",
    components: {
        SearchForm,
    },
    emits: ['search-movies'],
};
</script>

<template>
    <header>
        <div class="header-container d-flex align-items-center justify-content-between">
            <div class="left-header ps-3">
                <h1>BOOLFLIX</h1>
            </div>
            <div class="right-header pe-3">
                <SearchForm placeholder="Cerca Un film o serie TV" @submit-search="$emit('search-movies', $event)" />
            </div>
        </div>
    </header>
</template>

<style lang="scss" scoped >
/* Style here */
.header-container {
    height: 10vh;
    background-color: black;
}

.left-header {
    h1 {
        color: red;
    }
}
</style>