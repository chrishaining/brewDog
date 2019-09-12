<template lang="html">
<div v-if="beer" id="beer-detail">
  <p>{{beer.name}}</p>
  <img :src="beer.image_url" :alt="beer.name">
  <p>Tagline: {{beer.tagline}}</p>
  <p>Description: {{beer.description}}</p>
</div>
</template>

<script>
import { eventBus } from '../main'

export default {
  name: "beer-detail",
  props: ["beer"]
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
