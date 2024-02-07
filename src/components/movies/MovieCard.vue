<script>
export default {
    name: "MovieCard",
    props: {
        image: String,
        title: String,
        original: String,
        lang: String,
        vote: Number,
    }
};

</script>

<template>
    <div class="movie-card">
        <img class="img-fluid" :src="image" :alt="title">
        <h4>{{ title }}</h4>
        <p>{{ original }}</p>
        <p>{{ lang }}</p>
        <p>{{ vote }}</p>
    </div>
</template>

<style lang="scss" scoped >
.movie-card {
    color: white;
}

p {
    margin-bottom: 0;
}
</style>