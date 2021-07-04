<template>
  <div id="app" class="the-app">
    <TheCarousel msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import TheCarousel from './components/TheCarousel.vue'

export default {
  name: 'App',
  components: {
    TheCarousel
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

html,
body{
  height: 100%;
  font-family: "Roboto", san-serif;
}

#app{ 
  height: 100%;
}
</style>
