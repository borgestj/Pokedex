<template>
  <div class="container">
    <h1>{{ title }}</h1>
    <h4>Escolha a geração dos pokemons</h4>
    <div class="container options">
      <div class="choices" v-for="option in options" :key="option">
        <input @click="getGeneration(option)" type="radio" name="choices" :id="`generation${option}`" :value="option">
        <label :for="`generation${option}`">Generation {{option}}</label>
      </div>
    </div>
    <PokeList :items="generations"/>
  </div>
</template>

<script>
import PokeList from './PokeList.vue'

export default {
  props: {
    title: String
  },
  data () {
    return {
      generations: 1,
      options: [1, 2, 3, 4, 5, 6]
    }
  },

  methods: {
    getGeneration (value) {
      this.$http(`generation/${value}`)
        .then(response => {
          this.generations = response.data
        })
    }
  },

  components: {
    PokeList
  }
}
</script>
<style scoped lang="scss">
.options {
  display: flex;
  justify-content: center;
  align-items: center;

  .choices {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 15px;

    label {
      margin: 0 4px 0;
      font-size: 12px;
    }
  }
}
</style>
