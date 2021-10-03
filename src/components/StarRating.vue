<template>

  <div class="star_rating">
    <!--Bring the vote from a 1 to 10 scale to 1 to 5 scale (1/10 to 1/5) 
        using the proportion 1 : 10 = x : 5, we have x = 0.5 i.e x/2 i.e vote/2-
        -We round the number up when the the first number after the decimal point is >= 5 ( 2.6 to 3)
        we round the number down when it is <5 (2.4 to 2) by adding 0.5 to vote/2
        Ex.: Vote 7.6, 7.6/2 = 3.8, 4 stars 
        Credits: Myself -->
    <h6> Vote: {{vote}} </h6>
    <i v-for="star in stars" :key="star" :class="[ (vote/2 + 0.5 >= star) ? 'fas' : 'far', 'fa-star']"></i>
  </div>

</template>

<script>

export default {
  name: 'StarRating',

  props : {
    vote : Number
  },

  data : function(){
        return{
          stars : [1, 2, 3, 4, 5]
        }
    },

}
</script>


<style lang="scss">
@import '../style/general.scss';
</style>