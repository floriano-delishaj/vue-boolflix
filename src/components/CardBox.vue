<template>
  <div class="card-container col-lg-2 col-md-4 col-sm-6 col-12 d-flex justify-content-center my-3">
    <div class="card-box">
        <div class="info-film px-3">
            <div><strong>Titolo</strong>: {{film.title}}</div>
            <div><strong>Titolo originale</strong>: {{film.original_title}}</div>
            <div><strong>Lingua</strong>:
                <span v-if="film.original_language === null">Non dichiarata</span>
                <img v-else :src="langFlag(film.original_language)" alt="">
            </div>
            <!-- vote -->
            <div>
                <strong>Voto</strong>: 
                <span v-for="(star,i) in 5" :key="i">
                    <i v-if="(i <= stars())" class="fas fa-star"></i>
                    <i v-else class="far fa-star"></i>
                </span>
            </div>
            <div><strong>Overview</strong>: {{film.overview}}</div>
        </div>
        <a href="#">
            <img :src="`https://image.tmdb.org/t/p/original/${film.poster_path}`" alt="">
        </a>
    </div>
  </div>
</template>

<script>
export default {
    props: {
        film: Object,
    },
    methods: {
        langFlag(lang) {

            return `${`./flags/${lang}.png`}`
        },
        stars () {
            this.film.vote_average = Math.floor(this.film.vote_average)
            return this.film.vote_average / 2
        }
    }
};
</script>

<style lang="scss" scoped>
    @import '@/style/cardBox.scss';
</style>