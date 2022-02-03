<template>
  <main>
    <div class="container">
      <div class="row">
          <card-box 
            v-for="film in films"
            :key="film.id"
            :film="film"
        />
      </div>
    </div>
  </main>
</template>

<script>
import CardBox from "./CardBox.vue";

export default {
  components: {
      CardBox,
  },
  props: {
    films: Array,
  },
};
</script>

<style lang="scss" scoped>
@import "@/style/mainContainer.scss";
</style>