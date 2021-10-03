<template>
    <div id="searchbar">
            <!-- On keyup.enter or on click call the -search- function -->
            <input type="text" placeholder="Search the Film"
            v-on:keyup.enter="search" v-model="needle">
            <button v-on:click="search"> Search</button>         
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Searchbar',
    data : function(){
        return{
            needle : '',
            movieList : [],
            tvList : [],
            movieTvList : []
        }
    },

    methods : {
        search(){
            if(this.needle.trim() != ''){
                this.getMovieTv()
            } else {
                this.needle = ''
                this.movieTvList = ''
            }
        },

        /**
         * Make HTTP GET Request to an API for search/movies and search/tv using the 
         * needle as a query dynamic parameter and put it in the -movieTvList- array
         */
        getMovieTv(){
            let vm = this
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

                //Concat the movieList and tvList arrays in a unique array that will be used to the search result
                this.movieTvList = this.movieList.concat(this.tvList)
                
                //Check
                console.clear()
                console.log('Searchbar movieList:', this.movieList)
                console.log('Searchbar tvList:', this.tvList)
                console.log('Searchbar movieTvList:', this.movieTvList)
                
                //SEND movieTvList to Header
                vm.$emit('send', this.movieTvList)
            });
        },
    }
}
</script>

<style lang="scss" scoped>
@import '../style/general.scss';

</style>