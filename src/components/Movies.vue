<template>
    <section id="movies">
        Io Sono Movies 
    </section>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Movies',
    components: {
        
    },

    created : function() {
        //Make HTTP  GET Request to an API
        axios.get('https://api.themoviedb.org/3/search/movie?api_key=2c9b181fd830bd18b14d45907ca913b7',
        {
            params: {
                query : 'fight'
            }
        })
        .then((object) =>{
            console.log(object.data.results)
            
        });
    },

}
</script>


<style lang="scss" scoped>
#movies{
    height: 400px;
    background-color: burlywood;
}
</style>