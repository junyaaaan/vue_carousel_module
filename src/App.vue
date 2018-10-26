<template>
  <div id="app">
    <BannerCarousel />
  </div>
</template>

<script>
import BannerCarousel from './components/BannerCarousel.vue'

export default {
  name: 'app',
  components: {
    BannerCarousel,
  }
}
</script>

<style>
body {
  margin: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
