<script>
export default {
    name: "SearchForm",
    data: () => ({
        searchTerm: "",
    }),
    props: {
        placeholder: String,
    },

    emits: ['submit-search'],

    methods: {
        submitSearch() {
            this.$emit('submit-search', this.searchTerm);
            console.log("search option", this.searchTerm)
        }
    },
};
</script>

<template>
    <div>
        <form @submit.prevent="$emit('submit-search', searchTerm)" class="input-group">
            <input type="text" class="form-control" :placeholder="placeholder" v-model.trim="searchTerm">
            <button @click="$emit('submit-search', searchTerm)">Cerca</button>
        </form>
    </div>
</template>

<style lang="scss" scoped >
button {
    background-color: red;
    color: white;
    border: none;
    width: 80px;
    border-radius: 5px;
}
</style>