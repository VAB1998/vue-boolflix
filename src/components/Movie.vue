<template>
    <div class="col-4">

        <div class="movie">
            <h6> Title: {{ title }} </h6>
            <h6> Original Title: {{originalTitle}} </h6>
            <h6> Original Language: {{language}} </h6>
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
        vote : Number 
    },
}
</script>


<style lang="scss" scoped>
@import '../style/general.scss';
.movie{
    background-color: #0003;

}
</style>