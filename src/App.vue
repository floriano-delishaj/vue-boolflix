<template>
  <div id="app">
    <header-container @search="search"/>
    <img src="https://flagcdn.com/w20/it.png" alt="">
    <main-container :films="films"/>
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
      films : [],
      series: [],
      api_key: '6ca0c213ec5356631229b6b4eff3a90e',
    }
  },
  methods: {
    async callApi(type, query) {
      const params = {
        query: query,
        api_key: this.api_key,
      }

      const results = await axios.get(`https://api.themoviedb.org/3/search/${type}`, {params})
        .then( (res) =>{
          return res.data.results;
        })

      return results;
    },

    search(query) {
      this.searchFilms(query)
      this.searchSeries(query)
    },

    async searchFilms(query) {
      this.films = await this.callApi('movie', query)
    },

    async searchSeries(query) {
      this.series = await this.callApi('tv', query)
    }
  }
}

</script>

<style lang="scss">

  @import './style/main.scss';

</style>
