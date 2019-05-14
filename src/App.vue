<template>
  <div id="app">
    <cv></cv>
  </div>
</template>

<script>
import cv from "./views/cv.vue"
export default {
  name: 'app',
  components: {
    cv
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  /*https://coolbackgrounds.io/*/
  background-image: url('./assets/cool-background.png');
  background-size: cover;
}
</style>
