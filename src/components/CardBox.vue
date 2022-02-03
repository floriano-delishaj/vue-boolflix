<template>
  <div class="col-3 d-flex justify-content-center my-3">
    <div class="card-box">
        <div class="info-film px-3">
            <div><strong>Titolo</strong>: {{film.title}}</div>
            <div><strong>Titolo originale</strong>: {{film.original_title}}</div>
            <div><strong>Voto</strong>: {{film.vote_average}}</div>
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
    }
};
</script>

<style lang="scss" scoped>
    @import '@/style/cardBox.scss';
</style>