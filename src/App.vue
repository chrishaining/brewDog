<template lang="html">
  <div>
    <h1>BrewDog</h1>
    <beer-filter-form :beers="beers" />
    <beer-detail :beer="selectedBeer" :favouriteBeers="favouriteBeers" />
    <favourite-beers :favouriteBeers="favouriteBeers" />
  </div>

</template>

<script>
import BeerFilterForm from './components/BeerFilterForm'
import BeerDetail from './components/BeerDetail'
import FavouriteBeers from './components/FavouriteBeers'
import { eventBus } from './main'

export default {
  data() {
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
    }
  },
  components: {
    "beer-filter-form": BeerFilterForm,
    "beer-detail": BeerDetail,
    "favourite-beers": FavouriteBeers
  },
  mounted() {
    fetch('https://api.punkapi.com/v2/beers')
    .then(result => result.json())
    .then(beers => this.beers = beers)

    eventBus.$on('beer-selected', (beer) => {
      this.selectedBeer = beer;
    })
    eventBus.$on('favourite-beer', (beer) => {
      this.favouriteBeers.push(beer);
    })
  }
}
</script>

<style lang="css" scoped>

</style>
