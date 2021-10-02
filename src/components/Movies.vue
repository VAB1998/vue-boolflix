<template>
    <section id="movies">
        <div class="container-fluid">
            <div class="row justify-content-between align-items-center bg-dark mb-4">
                <div class="col-4">
                    <img src="https://fontmeme.com/permalink/211001/c072857f28ffed69c9266a55183f4c20.png" alt="Boolflix logo">
                </div>
                <div class="col-4">
                    <!-- ------Searchbar------ -->
                    <div id="searchbar">
                        <input type="text" placeholder="Search the Film"
                        v-on:keyup.enter="search" v-model="needle">
                        <button v-on:click="search"> Search</button>   
                    </div>
                </div>  
            </div>

            <div class="row gy-3">
                <!-- ------Movie------ -->
                <Movie v-for="(item) in completeList" :key="item.id" 
                :title="item.title" :originalTitle="item.original_title" :language="item.original_language" :vote="item.vote_average" 
                :tvTitle="item.name" :tvOriginalTitle="item.original_name" :imageSource="item.backdrop_path" />
            </div>

        </div>
        

    </section>
</template>

<script>
import Movie from './Movie.vue'
import axios from 'axios'


export default {
    name: 'Movies',

    components: {
        Movie
    },

    data : function(){
        return{

            needle : '',
            movieList : [],
            tvList : [],
            completeList : []
        }
    },

    methods :{
        search(){
            if(this.needle.trim() != ''){
                this.getMovieApi()
                this.getTvApi()
            } else {
                this.needle = ''
                this.completeList = ''
            }
        },

        /**
         * Make HTTP GET Request to an API for search/movies using the 
         * needle as a query dynamic parameter and put it in the -movieList- array
         */
        getMovieApi(){
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

                //Check
                console.clear()
                console.log('movieList:', this.movieList)
            });
        },

        /**
         * Make HTTP GET Request to an API for search/movies using the 
         * needle as a query dynamic parameter and put it in the -tvList- array
         */
        getTvApi(){
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

                //Check
                console.log('tvList:', this.tvList)
                
                //Concat the movieList and tvList arrays in a unique array that will be used to the search result
                this.completeList = this.movieList.concat(this.tvList)
                
                //Check
                console.log('completeList:', this.completeList)
            });
        }
    },   

    concatApi(){
        
    }
}
</script>


<style lang="scss" scoped>
@import '../style/general.scss';
#movies{
    height: 400px;
    
}
</style>