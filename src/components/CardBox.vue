<template>
  <div class="card-container col-lg-2 col-md-4 col-sm-6 col-12 d-flex justify-content-center my-3">
    <div class="card-box">
        <div class="info-film px-3">
            <div><strong>Titolo</strong>: {{film.title}}</div>
            <div><strong>Titolo originale</strong>: {{film.original_title}}</div>
            <div><strong>Lingua</strong>:
                <img v-if="lang.includes(film.original_language)" :src="`/flags/${film.original_language}.png`" alt="">
                <span v-else-if="film.original_language === null">Non dichiarata</span>
                <span class="text-uppercase" v-else>{{film.original_language}}</span>
            </div>
            <!-- vote -->
            <div>
                <strong>Voto</strong>: 
                <star-box :rate="film.vote_average"/>
                
            </div>
            <div><strong>Overview</strong>: {{film.overview}}</div>
        </div>
        <a href="#">
            <img v-if="film.poster_path != null" :src="`https://image.tmdb.org/t/p/original/${film.poster_path}`" alt="">
            <img v-else src="https://www.sirem.org/wp-content/uploads/2021/04/no-image.jpg" alt="">
        </a>
    </div>
  </div>
</template>

<script>
import StarBox from './StarBox.vue'

export default {
    components: {
        StarBox,
    },
    props: {
        film: Object,
    },
    data() {
        return {
            lang : ['al', 'de', 'en', 'es', 'fr', 'it']
        }
    }
};
</script>

<style lang="scss" scoped>
    @import '@/style/cardBox.scss';
</style>