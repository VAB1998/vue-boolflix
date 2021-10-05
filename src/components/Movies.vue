<template>
    <section id="movies">
        <div class="container">
            <div class="row row-cols-sm-1 row-cols-md-2 row-cols-xl-3 g-2">

                    <Movie v-for="(item) in movieTvList" :key="item.id" 
                    :title="item.title" :originalTitle="item.original_title" :language="item.original_language" :vote="item.vote_average" 
                    :tvTitle="item.name" :tvOriginalTitle="item.original_name" :imageSource="item.backdrop_path" :castList="item.castList" />
            </div>
        </div>
    </section>
</template>

<script>
import Movie from './Movie.vue'

export default {
    name: 'Movies',

    components: {
        Movie
    },

    props : {
        movieTvList : Array,
    },
}
</script>

<style lang="scss" scoped>
@import '../style/general.scss';

</style>