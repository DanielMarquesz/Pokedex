<template>
  <div id="app">
    <div v-for="(poke, index) in pokemons" :key="index">
      <!-- <h1>{{pokemons[index].name}}</h1>
      <h3>{{pokemons[index].url}}</h3><br> -->

      <Pokemom :name="poke.name" :url="poke.url" :num="index+1" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Pokemom from './components/Pokemon';

export default {
  name: 'App',

  data(){
      return {
        pokemons: []
    }
  },

  created: function() {
    axios.get("https://pokeapi.co/api/v2/pokemon?limit=100&offset=200").then((response)=>{
      
      this.pokemons = response.data.results;
      console.log(this.pokemons)
    })
  },

  components: {
    Pokemom
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
