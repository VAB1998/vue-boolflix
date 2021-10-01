<template>
  <div id="app">
    <Searchbar />
    <Movies />
  </div>
</template>

<script>
import Searchbar from './components/Searchbar.vue'
import Movies from './components/Movies.vue'

export default {
  name: 'App',
  components: {
    Searchbar,
    Movies    
  }
}
</script>
,
    Searchbar

<style lang="scss">

</style>

// API key: 2c9b181fd830bd18b14d45907ca913b7
// API Request: https://api.themoviedb.org/3/movie/550?api_key=2c9b181fd830bd18b14d45907ca913b7
// API Request Search a movie  https://api.themoviedb.org/3/search/movie?api_key=2c9b181fd830bd18b14d45907ca913b7&query=natale+sul+nilo