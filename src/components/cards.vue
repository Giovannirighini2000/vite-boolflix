<template>
    <li>
        <img :src="getImageUrl()" />
        <p>{{ card.title }}</p>
        <p>{{ card.original_title }}</p>
        <p>
            <img v-if="languageMapImg[card.original_language]" :src="languageMapImg[card.original_language]"
                class="img-size" />
            <span v-else>{{ card.original_language }}</span>
        </p>
        <p>{{ card.vote_average }}</p>
    </li>
</template>
  
<script>
export default {
    props: {
        card: {
            type: Object,
            required: true
        }
    },
    data() {
        return {
            languageMapImg: {
                en: '/flags/gb.jpg',
                fr: '/flags/fr.jpg',
                de: '/flags/de.png',
                es: '/flags/es.jpg',
                it: '/flags/it.jpg',

            }
        };
    },
    methods: {
        getImageUrl() {
            const baseUrl = 'https://image.tmdb.org/t/p/w500';
            const imagePath = this.card.backdrop_path;
            return baseUrl + imagePath;
        }
    }
};
</script>
<style lang="scss">
.img-size {
    width: 100px;
}
</style>