<template>
    <div id="searchbar">
        <!-- On keyup.enter or on click call the -search- function -->
        <!-- <input type="text" placeholder="Search a Film or a TV Series"
        v-on:keyup.enter="search" v-model="needle">
        <button class="btn" v-on:click="search">Search</button> -->
        <div class="input-group">
            <!-- SEND -needle- to App -->
            <input type="text" class="form-control" placeholder="Search a Film or a TV Series"
            v-on:keyup.enter="$emit('send', needle)" v-model.trim="needle">
            <button class="btn" v-on:click="$emit('send', needle)" >
                <span class="d-none d-md-inline">
                    Search 
                </span>
                <i class="fas fa-search d-md-none"></i>
                </button>
        </div>

    </div>
</template>

<script>

export default {
    name: 'Searchbar',
    data : function(){
        return{
            needle : '',
        }
    },
}
</script>

<style lang="scss" scoped>
@import '../style/general.scss';
@import '../style/variables.scss';

#searchbar{
    padding: 5px 0;
    button{
        background-color: $secondary_text_color;
        color: $primary_text_color;
        border-color: $secondary_text_color;
        border-radius: 0 5px 5px 0;
    }
}
</style>