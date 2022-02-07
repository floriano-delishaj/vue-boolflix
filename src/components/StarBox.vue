<template>
  <span>
    <span v-for="(star, i) in 5" :key="i">
      <i v-if="i <= stars()" class="fas fa-star"></i>
      <i v-else class="far fa-star"></i>
    </span>
  </span>
</template>

<script>
export default {
    props: {
        rate: Number
    },
  methods: {
    stars() {
      this.rate = Math.floor(this.rate);
      return this.rate / 2;
    },
  },
};
</script>

<style lang="scss" scoped>
</style>