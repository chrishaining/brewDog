<template lang="html">
  <div>
    <label for="beer-selection">Favourite beers: </label>
    <select v-on:change="handleSelect" v-model="favouriteBeer">
      <option value="" disabled selected>Select a favourite beer...</option>
      <option v-for="beer in favouriteBeers" :value="beer">{{beer.name}}</option>
    </select>
  </div>
</template>

<script>
import { eventBus } from '../main'

export default {
  name: "favourite-beers",
  data(){
    return {
      "favouriteBeer": {}
    }
  },
  props: ["favouriteBeers"],
  methods: {
    handleSelect(){
      eventBus.$emit("beer-selected", this.selectedBeer)
    }
  }

}
</script>

<style lang="css" scoped>
</style>
