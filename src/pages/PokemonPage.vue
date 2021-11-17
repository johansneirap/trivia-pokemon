<template>
    <h1 v-if="!pokemon">Search for a pokemon...</h1>
  <div v-else>
      <h1> Who is that Pokemon?</h1>
      <pokemon-picture 
      :pokemonID="pokemon.id" :showPokemon="showPokemon"/>
      <pokemon-options 
        :pokemons="pokemonsArr"
        @selection="checkAnswer"/>
    <div v-if="showAnswer" class="fade-in">
        <h2 >{{message}}</h2>
        <button @click="newGame"> Play again</button>
    </div>
  </div>
</template>

<script>
import PokemonOptions from '@/components/PokemonOptions.vue'
import PokemonPicture from '@/components/PokemonPicture.vue'

import getPokemonOptions from '@/helpers/getPokemonOptions'

getPokemonOptions()
export default {
  components: { PokemonPicture, PokemonOptions },

  data() {
      return {
          pokemonsArr : [],
          pokemon: null,
          showPokemon: false,
          showAnswer: false,
          message: ''
      }
  },
  methods: {
      async mixPokemonArr() {
          this.pokemonsArr = await getPokemonOptions()

          const rndInt = Math.floor(Math.random() * 4)
          this.pokemon = this.pokemonsArr[rndInt]
      },
      checkAnswer(selectedPokemonID){
          this.showPokemon = true
          this.showAnswer = true
          selectedPokemonID == this.pokemon.id ?
          this.message = `Great!! ${this.pokemon.name}` :
          this.message = `Oops, was ${this.pokemon.name}`
      },
      newGame(){
          this.showPokemon = false
          this.showAnswer = false
          this.pokemonsArr = []
          this.pokemon = null
          this.mixPokemonArr()
      }
  },
  mounted(){
      this.mixPokemonArr()
  }

}
</script>

<style>

</style>