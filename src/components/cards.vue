<template>
    <div class="relative-2">
        <div class="relative">
            <img class="img-card" :src="getImageUrl()" />
            <div class="card-info">
                <p class="white">{{ card.title || card.name }}</p>
                <p class="white">{{ card.original_title || card.original_name }}</p>
                <p>
                    <img v-if="languageMapImg[card.original_language]" :src="languageMapImg[card.original_language]"
                        class="img-size" />
                    <span v-else class="white">{{ card.original_language }}</span>
                </p>
                <p class="yellow-stars">{{ getStarRating(card.vote_average) }}</p>
            </div>
        </div>
    </div>
</template>
  
<script>
export default {
    props: {
        card: {
            type: Object,
            required: true,
        },
    },
    data() {
        return {
            languageMapImg: {
                en: "/flags/gb.jpg",
                fr: "/flags/fr.jpg",
                de: "/flags/de.png",
                es: "/flags/es.jpg",
                it: "/flags/it.jpg",
            },
        };
    },
    methods: {
        getImageUrl() {
            const baseUrl = "https://image.tmdb.org/t/p/w342";
            const imagePath = this.card.backdrop_path;
            if (imagePath) {
                return baseUrl + imagePath;
            } else {

                return "https://www.ilcorrieredellacitta.com/wp-content/uploads/2020/05/netflix-film-serie-tv-streaming-catalogo-uscite.jpg";

            }
        },
        getStarRating(voteAverage) {
            const fullStar = '\u2605';
            const emptyStar = '\u2606';
            const rating = Math.round(voteAverage / 2);
            return fullStar.repeat(rating) + emptyStar.repeat(5 - rating);
        }


    },
};
</script>
  
<style lang="scss" scoped>
.img-size {
    width: 30px;
}

.img-card {
    width: 300px;
    position: relative;
    height: 170px;
}

.white {
    color: white;
}

.card-info {
    position: absolute;
    top: 8%;
    left: 0;
    visibility: hidden;
    background-color: rgba(0, 0, 0, 0.8);
    padding: 10px;
    transition: visibility 1.5s, opacity 0.2s ease-in-out;
}

.relative-2:hover .card-info {
    visibility: visible;
    opacity: 1;
}

.relative-2:hover .img-card {
    visibility: hidden;
}

.card-info p {
    margin: 5px 0;
}

.card-info img {
    margin-right: 5px;
}

.relative {
    position: relative;
}

.yellow-stars {
    color: yellow;
}
</style>
  

  
