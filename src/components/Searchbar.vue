<template>
    <div id="searchbar">
            <!-- <input type="text" placeholder="Search the Film"
            v-on:keyup.enter="$emit('searchMovie', needle)" v-model="needle">
            <button v-on:click="$emit('searchMovie', needle)"> Search </button>         -->
    </div>
</template>

<script>


export default {
    name: 'Searchbar',
    data : function(){
        return{
            needle : ''
        }
    },


}


</script>


<style lang="scss" scoped>
@import '../style/general.scss';
#searchbar{
    float: right;
}
</style>