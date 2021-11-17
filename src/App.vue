<template>
  <!-- <img class="fade-in" alt="Vue logo" src="./assets/logo.png"> -->
  <PokemonPage />
</template>

<script>
import PokemonPage from './pages/PokemonPage.vue'

export default {
  name: 'App',
  components: {
    PokemonPage
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
