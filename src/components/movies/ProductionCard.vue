<script>
import { imgBaseEndpoint } from '../data/index.js';
export default {
    name: "ProductionCard",
    data: () => ({
        imgBaseEndpoint,
    }),
    props: {
        production: Object,
    },

    computed: {
        title() {
            return this.production.title || this.production.name;
        },

        originalTitle() {
            return this.production.original_title || this.production.original_name;
        },

        lang() {
            return this.production.original_language;
        },

        poster() {
            return `${this.imgBaseEndpoint}${this.production.poster_path}`;
        },

        hasFlag() {
            const flags = ["it", "en"];
            return flags.includes(this.lang);
        },

        flagSrc() {
            const url = new URL(`../../assets/img/${this.lang}.png`, import.meta.url);
            console.log(url.href);
            return url.href;
        },
    }
};

</script>

<template>
    <div class="production-card">
        <ul class="list-unstyled">
            <img :src="poster" :alt="title">
            <li>{{ title }}</li>
            <li>{{ originalTitle }}</li>
            <li>
                <img v-if="hasFlag" :src="flagSrc" :alt="lang">
                <span v-else> {{ lang }}</span>
            </li>
            <li>{{ production.vote_avarage }}</li>
        </ul>
    </div>
</template>

<style lang="scss" scoped >
.production-card {
    color: white;

    ul li img {
        max-width: 40px;
    }
}
</style>