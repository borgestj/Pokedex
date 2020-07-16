<template>
  <div class="hello">
    <h1>{{ title }}</h1>
    <h4>Escolha a geração dos pokemons</h4>
    <div class="teste">
      <form class="choices" v-for="choice in choices" :key="choice">
        <input @click="getGeneration(choice)" type="radio" name="choice" :id="choice" :value="choice">
        <label :for="choice">Generation {{choice}}</label>
      </form>
    </div>
    <div class="generations">
      <p>{{ generations.name }}</p>
      <ul class="pokemons" v-for="pokemons in generations.pokemon_species" :key="pokemons.id">
        <li>{{ pokemons.name }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: String
  },
  data () {
    return {
      generations: [],
      choices: [1, 2, 3, 4, 5, 6]
    }
  },

  methods: {
    getGeneration (value) {
      console.log(value)
      this.$http(`generation/${value}`)
        .then(response => {
          this.generations = response.data
          console.log(this.generations)
        })
    }
  }
}
</script>
<style scoped lang="scss">
.teste {
  display: flex;
  justify-content: center;
  align-items: center;
  .choices {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 15px;
  }
}

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
