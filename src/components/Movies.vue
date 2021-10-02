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
                <Movie v-for="(item) in movieList" :key="item.id" 
                :title="item.title" :originalTitle="item.original_title" :language="item.original_language" :vote="item.vote_average" />
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
            movieList : []
        }
    },

    methods :{
        search(){
            if(this.needle.trim() != ''){
                 //Make HTTP  GET Request to an API
                axios.get('https://api.themoviedb.org/3/search/movie?api_key=2c9b181fd830bd18b14d45907ca913b7',
                {
                    params: {
                        query : this.needle,
                    }
                })
                .then((object) =>{
                    this.movieList = object.data.results
                    //Check
                    console.clear()
                    console.log('API Respone: ', object.data.results)
                    console.log('MovieList:', this.movieList)
                });
            } else {
                this.needle = ''
                this.movieList = ''
            }
        }
    },   
}
</script>


<style lang="scss" scoped>
@import '../style/general.scss';
#movies{
    height: 400px;
    
}
</style>