<script>
import SearchForm from './SearchForm.vue';
import { store } from './data/store.js';
export default {
    name: "AppHeader",
    data: () => ({
        store,
    }),
    components: {
        SearchForm,
    },
    emits: ['search-production']
};
</script>

<template>
    <header>
        <div class="header-container d-flex align-items-center justify-content-between">
            <div class="left-header ps-3">
                <h1>BOOLFLIX</h1>
            </div>
            <div class="right-header pe-3">
                <SearchForm placeholder="Cerca Un film o serie TV" @submit-search="$emit('search-production', $event)" />
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