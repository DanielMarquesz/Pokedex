<template>
  <div>
    
    <!-- <h1>Nome: {{ name | upper }}</h1>
    <small>Link: {{ url }}</small>
    <h1>Número: {{ num }}</h1> -->

    <div class="card cartao">
      <div class="card-image">
        <figure class="">
          <img
            :src="pokemon.front"
            alt="Placeholder image"
          />
        </figure>
      </div>
      <div class="card-content">
        <div class="media">          
          <div class="media-content">
            <p class="title is-4">{{ name | upper }}</p>
            <p class="subtitle is-6">{{ pokemon.type }}</p>
          </div>
        </div>

        <div class="content">
          
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  created: function () {
    axios.get(this.url).then((res) => {
      this.pokemon.type = res.data.types[0].type.name;
      this.pokemon.front = res.data.sprites.front_default;
      this.pokemon.back = res.data.sprites.back_default;
      console.log(this.pokemon);
    });
  },

  data() {
    return {
      pokemon: {
        type: '',
        front: '',
        back: ''
      },
    };
  },

  props: {
    name: String,
    url: String,
    num: Number,
  },

  filters: {
    upper: function (value) {
      var newName = value[0].toUpperCase() + value.slice(1);
      return newName;
    },
  },
};
</script>

<style scoped>

.cartao{
  box-shadow: -0.1rem 0.1rem 2rem;
  margin-top: 1.8rem;
}

</style>
