<template>
    <div class="col-4">

        <div class="movie h-100 p-3">
            <h6> Title: {{ title }} {{tvTitle}} </h6>
            <h6> Original Title: {{originalTitle}} {{tvOriginalTitle}} </h6>
            <h6 v-if="language == 'en'">
                <img :src="`https://www.countryflags.io/gb/flat/64.png`">
                <img :src="`https://www.countryflags.io/us/flat/64.png`">
            </h6>
            <h6 v-else>
                <img :src="`https://www.countryflags.io/${language}/flat/64.png`" :alt="language">
            </h6>
            <h6> Vote: {{vote}} </h6> 
            <img v-if="imageSource != Null" :src="`https://image.tmdb.org/t/p/w342${imageSource}`" alt="Image Poster">
            <img v-else :src="`https://dummyimage.com/342x192/273696/fff.jpg&text=Movie+Poster+Coming+Soon`" alt="Image Poster">
        </div>
        
    </div>

</template>

<script>

export default {
    name: 'Movie',

    props : {
        title : String,
        originalTitle : String, 
        language : String, 
        vote : Number,
        tvTitle : String,
        tvOriginalTitle : String,
        imageSource : {
            type : String,

        }
    },
}
</script>


<style lang="scss" scoped>
@import '../style/general.scss';
.movie{
    background-color: #1958ec33;

}
</style>