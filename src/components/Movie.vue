<template>
    <div class="col d-flex justify-content-center">
        <div class="movie_card h-100">
            <div class="inner_movie_card">
                <div class="back_movie_card p-2">
                    <h5> Title: {{ title ? title :tvTitle}} </h5>
                    <h6> Original Title: {{originalTitle ? originalTitle : tvOriginalTitle}} </h6>
                    <!-- Add language flats using the ISO 3166 Code of the Countries Ex.: Italy Code=it Italy Language=it  -->
                    <div v-if="language == 'en'">
                        <img :src="`https://www.countryflags.io/gb/flat/64.png`">
                        <img :src="`https://www.countryflags.io/us/flat/64.png`">
                    </div>
                    <div v-else >                
                        <img :src="`https://www.countryflags.io/${language}/flat/64.png`" :alt="`Language : ${language}`">
                    </div>

                    <StarRating :vote="vote" />
            
                </div>
                <div class="front_movie_card">
                    <img v-if="imageSource != null" :src="`https://image.tmdb.org/t/p/w342${imageSource}`" alt="Image Poster">
                    <img v-else :src="`https://dummyimage.com/342x192/525252/fff.jpg&text=Movie+Poster+Coming+Soon`" alt="Image Poster">
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import StarRating from './StarRating.vue'

export default {
    name: 'Movie',

    components: {
        StarRating
    },

    props : {
        title : String,
        originalTitle : String, 
        language : String, 
        vote : Number,
        tvTitle : String,
        tvOriginalTitle : String,
        imageSource : String,
    },
}
</script>


<style lang="scss" scoped>
@import '../style/general.scss';
@import '../style/variables.scss';
.movie_card{
    // Spacing and Dimesions
    height: 142px;
    width: 342px;
    //Style
    color: $primary_text_color; 
    //Flip card Effect Settings
    background-color: transparent;

    .inner_movie_card{
        //Flip card Effect Settings
        width: 100%;
        height: 100%;
        position: relative;
        transform-style: preserve-3d;
        transition: transform 0.8s;
        
    }
        &:hover .inner_movie_card{
            //Flip card Effect Settings
            transform: rotateY(180deg);
        }

    .front_movie_card,
    .back_movie_card{
        //Flip card Effect Settings
        backface-visibility: hidden;
        -webkit-backface-visibility: hidden; /* Safari */
    }

    .back_movie_card{
        //Style
        background-color: #2d3436;
        background-image: linear-gradient(315deg, #2d3436 0%, #000000 74%);
        overflow-y: auto;
        //Flip card Effect Settings
        position: absolute;
        height: 100%;
        width: 100%;
        transform: rotateY(180deg);
    }
}
</style>