<template>
    <section id="movies">
        <div class="container">
            <div class="row row-cols-sm-1 row-cols-md-2 row-cols-xl-3 g-2">
                    <!--Iterate throught the movieTvList(movieList + tvList) array obtained from API 
                    Pass the datas via props of movieTvList -->
                    <Movie v-for="(movieItem) in movieList" :key="movieItem.id" 
                    :movieTitle="movieItem.title" :movieOriginalTitle="movieItem.original_title" :movieLanguage="movieItem.original_language" :movieVote="movieItem.vote_average" 
                    :movieImageSource="movieItem.backdrop_path" :movieId="movieItem.id"/>


                    <Movie v-for="(tvItem) in tvList" :key="tvItem.id" 
                    :tvTitle="tvItem.name" :tvOriginalTitle="tvItem.original_name" :tvLanguage="tvItem.original_language" :tvVote="tvItem.vote_average" 
                    :tvImageSource="tvItem.backdrop_path" :tvId="tvItem.id"/>



                    <!-- <Movie v-for="(item) in movieTvList" :key="item.id" 
                    :title="item.title" :originalTitle="item.original_title" :language="item.original_language" :vote="item.vote_average" 
                    :tvTitle="item.name" :tvOriginalTitle="item.original_name" :imageSource="item.backdrop_path" :id="item.id"/> -->
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
        movieList : Array,
        tvList : Array
    },
}
</script>

<style lang="scss" scoped>
@import '../style/general.scss';

</style>