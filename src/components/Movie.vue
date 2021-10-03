<template>
    <div class="col">
        <div class="movie h-100">
            <h6> Title: {{ title }} {{tvTitle}} </h6>
            <h6> Original Title: {{originalTitle}} {{tvOriginalTitle}} </h6>
            <!-- Add language flats using the ISO 3166 Code of the Countries Ex.: Italy Code=it Italy Language=it  -->
            <div v-if="language == 'en'">
                <img :src="`https://www.countryflags.io/gb/flat/64.png`">
                <img :src="`https://www.countryflags.io/us/flat/64.png`">
            </div>
            <div v-else >                
                <img :src="`https://www.countryflags.io/${language}/flat/64.png`" :alt="`Language : ${language}`">
            </div>

            <StarRating :vote="vote" />

            <img v-if="imageSource != null" :src="`https://image.tmdb.org/t/p/w342${imageSource}`" alt="Image Poster">
            <img v-else :src="`https://dummyimage.com/342x192/273696/fff.jpg&text=Movie+Poster+Coming+Soon`" alt="Image Poster">
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
.movie{
    background-color: #1958ec33;
}
</style>