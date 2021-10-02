<template>
  <div id="app">
    <!-- <Searchbar @searchMovie="storeNeedle" /> -->
    <Movies :needle="needle" />
  </div>
</template>

<script>
// import Searchbar from './components/Searchbar.vue'
import Movies from './components/Movies.vue'

export default {
  name: 'App',

  data : function(){
        return{
          needle : ''
        }
    },

  components: {
    // Searchbar,
    Movies    
  },

  methods :{
    // storeNeedle(needle){
    //   this.needle = needle
    //   // console.log(needle)
    //   // console.log(this.needle)
    // }
  }
}
</script>


<style lang="scss">
@import './style/general.scss';
</style>

// API key: 2c9b181fd830bd18b14d45907ca913b7
// API Request: https://api.themoviedb.org/3/movie/550?api_key=2c9b181fd830bd18b14d45907ca913b7
// API Request Search a movie  https://api.themoviedb.org/3/search/movie?api_key=2c9b181fd830bd18b14d45907ca913b7&query=natale+sul+nilo

