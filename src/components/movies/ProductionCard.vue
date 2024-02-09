<script>
import { imgBaseEndpoint } from '../data/index.js';
export default {
    name: "ProductionCard",
    data: () => ({
        imgBaseEndpoint,
        stars: 5,
        minStars: 1,
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

        vote() {
            return this.production.vote_average;
        },


        hasPoster() {
            return !this.production.poster_path;
        },

        hasFlag() {
            const flags = ["it", "en", "es", "de", "fr", "ko", "ja", "cn", "pt"];
            return flags.includes(this.lang);
        },

        flagSrc() {
            const url = new URL(`../../assets/img/${this.lang}.png`, import.meta.url);
            console.log(url.href);
            return url.href;
        },
    },

    methods: {
        getRealVote(vote) {
            const wholeNumber = Math.floor(vote)
            if (wholeNumber >= 1 && wholeNumber <= 2) {
                return 1;
            } else if (wholeNumber > 2 && wholeNumber <= 4) {
                return 2;
            } else if (wholeNumber > 4 && wholeNumber <= 6) {
                return 3;
            } else if (wholeNumber > 6 && wholeNumber <= 8) {
                return 4;
            } else if (wholeNumber > 8 && wholeNumber <= 10) {
                return 5;
            }
        },
    }
};

</script>

<template>
    <div class="production-card">
        <ul class="list-unstyled">
            <li>
                <img v-if="hasPoster" src="`../../assets/img/boolflix-image-not-found.png`" :alt="title" class="poster-img">
                <img v-else :src="poster" :alt="title" class="poster-img">
            </li>
            <li>{{ title }}</li>
            <li>{{ originalTitle }}</li>
            <li class="flag">
                <img v-if="hasFlag" :src="flagSrc" :alt="lang">
                <span v-else> {{ lang }}</span>
            </li>
            <li v-if="getRealVote(vote) > minStars">
                <i v-for="(star, i) in stars" :key="i"
                    :class="{ 'fas fa-star': star <= getRealVote(vote), 'far fa-star': star > getRealVote(vote) }"></i>
            </li>
            <li v-else>
                <i v-for="i in stars" :key="i" class="far fa-star"></i>
            </li>
        </ul>
    </div>
</template>

<style lang="scss" scoped >
.production-card {
    color: white;
}

.poster-img {
    height: 513px;
}

.flag img {
    max-width: 40px;
}
</style>