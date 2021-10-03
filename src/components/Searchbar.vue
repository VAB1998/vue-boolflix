<template>
    <div id="searchbar">
        <!-- On keyup.enter or on click call the -search- function -->
        <!-- <input type="text" placeholder="Search a Film or a TV Series"
        v-on:keyup.enter="search" v-model="needle">
        <button class="btn" v-on:click="search">Search</button>      -->
        <div class="input-group">
            <input type="text" class="form-control" placeholder="Search a Film or a TV Series"
            v-on:keyup.enter="search" v-model="needle">
            <button class="btn" v-on:click="search" >Search</button>
        </div>

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
            let vn = this
            if(this.needle.trim() != ''){
                this.getMovieTv()
                this.needle = this.needle.trim()
            } else {
                this.needle = ''
                this.movieTvList = []
                //SEND movieTvList to Header
                vn.$emit('send', this.movieTvList)
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
@import '../style/variables.scss';

#searchbar{
    input{
        width: 80%;;
        height: 100%;
    }
    button{
        background-color: $secondary_text_color;
        color: $primary_text_color;
        border-color: $secondary_text_color;
        border-radius: 0 5px 5px 0;
        width: 20%;
        // height: 100%;
    }
}
</style>