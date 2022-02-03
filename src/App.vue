<template>
  <div id="app">
    <header-container />
    {{getFilm()}}
    <main-container />
  </div>
</template>

<script>
import axios from 'axios'

import HeaderContainer from './components/HeaderContainer.vue'
import MainContainer from './components/MainContainer.vue'


export default {
  name: 'App',
  components: {
    HeaderContainer,
    MainContainer
  },
  props: {

  },
  data() {
    return {

    }
  },
  methods: {
    getFilm() {

      let films = [];

      axios.get('https://api.themoviedb.org/3/search/movie?query=title&api_key=6ca0c213ec5356631229b6b4eff3a90e')
          .then ( (res) => {
            this.films = res.data.results
          })
          return films
    }
  }
}
</script>

<style lang="scss">

  @import './style/main.scss';

</style>
