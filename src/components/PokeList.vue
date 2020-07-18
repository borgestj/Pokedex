<template>
  <div class="container">
    <p>{{ items.name }}</p>
    <div class="cards">
      <div class="card" v-for="pokemons in items.pokemon_species" :key="pokemons.id">
        <img class="image" :src="`https://img.pokemondb.net/artwork/${pokemons.name}.jpg`" :alt="pokemons.name">
        <h3>{{ pokemons.name }}</h3>
      </div>
    </div>
  </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {
  props: {
    items: {}
  }
}
</script>

<style lang="scss" scoped>
.container {
  padding-bottom: 200px;
  .cards {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;

    .card {
      box-shadow: 0px 0px 6px 1px rgba(0, 0, 0, 0.2);
      padding: 10px;
      margin: 10px;
      width: 240px;

      .image {
        padding: 10px;
        width: 220px;
        height: 249px;
      }

      h3 {
        color: #151515;
      }
    }
  }
}

@media (max-width: 1025px) {
  .cards {
    grid-template-columns: 1fr 1fr 1fr;
  }
}

@media (max-width: 770px) {
  .cards {
    grid-template-columns: 1fr 1fr;

    .card {
      margin: 20px auto;
    }
  }
}

@media (max-width: 500px) {
  .cards {
    grid-template-columns: 1fr;

    .card {
      margin: 10px auto;
    }
  }
}

</style>
