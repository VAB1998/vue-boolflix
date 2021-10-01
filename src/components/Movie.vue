<template>
    <section class="movie">
        {{title}} -- {{originalTitle}} -- {{language}} -- {{vote}}
        
    </section>
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

    data : function(){
        return{
        }
    },

    methods :{
        
    },
}
</script>


<style lang="scss" scoped>
.movie{
    
    background-color: cornflowerblue;
    border: 1px solid black;
    display: inline-block;
}
</style>