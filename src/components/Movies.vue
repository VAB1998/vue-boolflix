<template>
    <section id="movies">
        <h1 class="text-danger">Io Sono Movies </h1>
        <div>
            <input type="text" placeholder="Search the Film"
            v-on:keyup.enter="search()" v-model="textToSearch">
            <button v-on:click="search()"> Search </button>
        </div>

        <Movie v-for="(item) in movieList" :key="item.id" 
        :title="item.title" :originalTitle="item.original_title" :language="item.original_language" :vote="item.vote_average" />

        {{textToSearch}}
    </section>
</template>
// Titolo
// Titolo Originale
// Lingua
// Voto

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
            textToSearch: '',
            movieList : []
        }
    },

    methods :{
        search(){
            if(this.textToSearch.trim() != ''){
                 //Make HTTP  GET Request to an API
                axios.get('https://api.themoviedb.org/3/search/movie?api_key=2c9b181fd830bd18b14d45907ca913b7',
                {
                    params: {
                        query : this.textToSearch
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
                this.textToSearch = ''
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
    background-color: burlywood;
    
}
</style>