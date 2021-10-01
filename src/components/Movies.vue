<template>
    <section id="movies">
        Io Sono Movies 

            <input type="text" v-model="textToSearch">
            <button v-on:click="search()"> Search </button>

        {{textToSearch}}
    </section>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Movies',
    components: {
        
    },
    data : function(){
        return{
            textToSearch: '',
        }
    },

    methods :{
        search(){
            //Make HTTP  GET Request to an API
            axios.get('https://api.themoviedb.org/3/search/movie?api_key=2c9b181fd830bd18b14d45907ca913b7',
            {
                params: {
                    query : this.textToSearch
                }
            })
            .then((object) =>{
                // console.clear()
                console.log('API Respone: ', object.data.results)
            });
        }
    },
    created : function() {
        console.log('Created')
        
    },

    computed : {
        
    }

}
</script>


<style lang="scss" scoped>
#movies{
    height: 400px;
    background-color: burlywood;
}
</style>