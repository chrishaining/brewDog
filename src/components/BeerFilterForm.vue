<template lang="html">
  <div>
    <label for="beer-selection">Select a beer: </label>
    <select v-on:change="handleSelect" v-model="selectedBeer">
      <option value="" disabled selected>Select a beer...</option>
      <option v-for="beer in beers" :value="beer">{{beer.name}}</option>
    </select>
  </div>
</template>

<script>
import { eventBus } from '../main'

export default {
  name: "beer-filter-form",
  data(){
    return {
      "selectedBeer": {}
    }
  },
  props: ["beers"],
  methods: {
    handleSelect(){
      eventBus.$emit("beer-selected", this.selectedBeer)
    }
  }

}
</script>

<style lang="css" scoped>
</style>
