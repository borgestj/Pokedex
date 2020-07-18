<template>
  <div class="home">
    <Pokedex title="Pokedex"/>
  </div>
</template>

<script>
import Pokedex from '@/components/Pokedex.vue'

export default {
  name: 'Home',
  components: {
    Pokedex
  }
}
</script>

<style lang="scss" scoped>
.home {
  padding-top: 20px;
  background-image: url("pokemon.png");
  background-repeat: no-repeat;
  background-size: 100%;
}
</style>
