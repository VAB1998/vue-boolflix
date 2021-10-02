<template>
    <div class="col-4">

        <div class="movie">
            <h6> Title: {{ title }} {{tvTitle}} </h6>
            <h6> Original Title: {{originalTitle}} {{tvOriginalTitle}} </h6>
            <h6 v-if="language == 'en'">
                <img :src="`https://www.countryflags.io/gb/flat/64.png`">
                <img :src="`https://www.countryflags.io/us/flat/64.png`">
            </h6>
            <h6 v-else>
                <img :src="`https://www.countryflags.io/${language}/flat/64.png`">
            </h6>
            
            <h6> Vote: {{vote}} </h6> 
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
    },
}
</script>


<style lang="scss" scoped>
@import '../style/general.scss';
.movie{
    background-color: #0003;

}
</style>