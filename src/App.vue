<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <appplication></appplication>
    <!-- <movie></movie> -->
    <!-- <seat></seat> -->
  </div>
</template>

<script>
import Appplication from './components/Appplication.vue'
// import Movie from './components/Movie.vue'
// import Seat from './components/Seat.vue'
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld
    Appplication,
    // Movie,
    // Seat
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
