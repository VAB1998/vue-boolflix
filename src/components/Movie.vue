<template>
    <div class="col-4">

        <div class="movie h-100 p-3">
            <h6> Title: {{ title }} {{tvTitle}} </h6>
            <h6> Original Title: {{originalTitle}} {{tvOriginalTitle}} </h6>
            <div v-if="language == 'en'">
                <img :src="`https://www.countryflags.io/gb/flat/64.png`">
                <img :src="`https://www.countryflags.io/us/flat/64.png`">
            </div>
            <div v-else >
                <img :src="`https://www.countryflags.io/${language}/flat/64.png`" :alt="`Language : ${language}`">
            </div>
            <h6> Vote: {{vote}} </h6>
            <!-- Work in progress -->
            <h6>
                <!--Bring the vote from a 1 to 10 scale to 1 to 5 scale (1/10 to 1/5) 
                    using the proportion 1 : 10 = x : 5, we have x = 0.5 i.e x/2 i.e vote/2-
                    -We round the number up when the the first number after the decimal point is >= 5 ( 2.6 to 3)
                    we round the number down when it is <5 (2.4 to 2) by adding 0.5 to vote/2
                    Ex.: Vote 7.6, 7.6/2 = 3.8, 4 stars 
                    Credits: Myself
                -->
                <i v-for="star in stars" :key="star" :class="[ (vote/2 + 0.5 >= star) ? 'fas' : 'far', 'fa-star']"></i>
            </h6>


            <!-- /Work in progress -->
            <img v-if="imageSource != null" :src="`https://image.tmdb.org/t/p/w342${imageSource}`" alt="Image Poster">
            <img v-else :src="`https://dummyimage.com/342x192/273696/fff.jpg&text=Movie+Poster+Coming+Soon`" alt="Image Poster">
        </div>
        
    </div>

</template>

<script>

export default {
    name: 'Movie',

    data : function(){
        return{

            stars : [1, 2, 3, 4, 5]
        }
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