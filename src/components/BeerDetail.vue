<template lang="html">
<div v-if="beer" id="beer-detail">
  <p>{{beer.name}}</p>
  <img :src="beer.image_url" :alt="beer.name">
  <p>Tagline: {{beer.tagline}}</p>
  <p>Description: {{beer.description}}</p>
  <button v-if="!favouriteBeers.includes(beer)" v-on:click="addToFavourites"> ❤️ </button>
</div>
</template>

<script>
import FavouriteBeers from './FavouriteBeers'
import { eventBus } from '../main'

export default {
  name: "beer-detail",
  props: ["beer", "favouriteBeers"],
  methods: {
    addToFavourites: function() {
      eventBus.$emit("favourite-beer", this.beer)
    }
  }
}
</script>

<style lang="css" scoped>

#beer-detail {
  border: 2px solid black;
  background-color: lightskyblue;
  text-align: center;
}

img {
  height: 100px;
  width: 30px;
}

</style>
