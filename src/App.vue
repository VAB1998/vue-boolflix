<template>
  <div id="app">
    <!-- RECEIVE -needle- from Header...Searchbar -->
    <Header @send="search"/>
    <!-- SEND movieTvList to Movies -->
    <Movies :movieTvList="movieTvList" :movieList="movieList" :tvList="tvList" />
  </div>
</template>

<script>
import Movies from './components/Movies.vue'
import Header from './components/Header.vue'
import axios from 'axios'

export default {
  name: 'App',

  data : function(){
        return{
          needle : '',
          movieList : [],
          tvList : [],
          movieTvList : [],
        }
    },

  components: {
    Header,
    Movies    
  },

  methods :{
    search(needle){
            this.needle = needle
            if(needle != ''){
                this.getMovieTv()
            } else {
                this.needle = ''
                this.movieTvList = []
            }
        },

        /**
         * Make HTTP GET Request to an API for search/movies and search/tv using the 
         * needle as a query dynamic parameter and put it in the -movieTvList- array
         */
        getMovieTv(){
            //Make HTTP GET Request to an API for search/movies
            axios.get('https://api.themoviedb.org/3/search/movie',
            {
                params: {
                    api_key : '2c9b181fd830bd18b14d45907ca913b7',
                    query : this.needle,
                }
            })
            .then((object) =>{
                //Put the result of the Request in movieList array
                this.movieList = object.data.results

                //Add the CastList in each movie Item
                for(let movieItem of this.movieList){
                  axios.get(`https://api.themoviedb.org/3/movie/${movieItem.id}/credits`,
                  {
                    params: {
                        api_key : '2c9b181fd830bd18b14d45907ca913b7',
                    }
                  })
                  .then((object) =>{

                    let castList = []

                      let i = 0
                      while(i < 5 && object.data.cast[i] != undefined){
                        castList.push(object.data.cast[i].original_name)
                        i++

                      }
                      movieItem.castList = castList
                  });
                }

            });

            
            

            //Make HTTP GET Request to an API for search/tv
            axios.get('https://api.themoviedb.org/3/search/tv',
            {
                params: {
                    api_key : '2c9b181fd830bd18b14d45907ca913b7',
                    query : this.needle,
                }
            })
            .then((object) =>{
                //Put the result of the Request in tvList array
                this.tvList = object.data.results

                //Add the CastList in each TV Item
                for(let tvItem of this.tvList){
                  axios.get(`https://api.themoviedb.org/3/tv/${tvItem.id}/credits`,
                  {
                    params: {
                        api_key : '2c9b181fd830bd18b14d45907ca913b7',
                    }
                  })
                  .then((object) =>{

                    let castList = []

                      let i = 0
                      while(i < 5 && object.data.cast[i] != undefined){
                        castList.push(object.data.cast[i].original_name)
                        i++
                      }
                      tvItem.castList = castList
                  });
                }

                //Concat the movieList and tvList arrays in a unique array that will be used to the search result
                this.movieTvList = this.movieList.concat(this.tvList)
                
                //Check
                // console.clear()
                console.log('Movie List:', this.movieList)
                console.log('Tv List:', this.tvList)
                console.log('Movie and TvList:', this.movieTvList)
            });
        },
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


// Search the cast
//https://api.themoviedb.org/3/movie/42432/credits?api_key=2c9b181fd830bd18b14d45907ca913b7
//API Request Search Movies and TV Series: 
//https://api.themoviedb.org/3/search/multi?api_key=2c9b181fd830bd18b14d45907ca913b7&query=natale+sul+nilo