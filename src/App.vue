<template>
  <div id="app">
    <!-- RECEIVE movieTvList from Header...Searchbar -->
    <Header @send="receive"/>
    <!-- SEND movieTvList to Movies -->
    <Movies :movieTvList="movieTvList" />
  </div>
</template>

<script>
import Movies from './components/Movies.vue'
import Header from './components/Header.vue'

export default {
  name: 'App',

  data : function(){
        return{
          movieTvList : []
        }
    },

  components: {
    Header,
    Movies    
  },

  methods :{
    receive(movieTvList){
            this.movieTvList = movieTvList
            console.log('App movieTvList:', this.movieTvList)
        }
  }
}
</script>

<style lang="scss">
@import './style/general.scss';
#app{
  min-height: 100vh;
  padding-bottom: 20px;
}
</style>

// API key: 2c9b181fd830bd18b14d45907ca913b7
// API Request: https://api.themoviedb.org/3/movie/550?api_key=2c9b181fd830bd18b14d45907ca913b7
// API Request Search a movie  https://api.themoviedb.org/3/search/movie?api_key=2c9b181fd830bd18b14d45907ca913b7&query=natale+sul+nilo