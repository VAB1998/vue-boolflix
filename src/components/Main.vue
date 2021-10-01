<template>
  <main>
    Io sono Main
      <Movies />
  </main>
</template>

<script>
import Movies from './Movies.vue'

export default {
  name: 'Main',
  components: {
    Movies
  }
}
</script>


<style lang="scss" scoped>
main{
  padding: 6px;
  background-color: brown;
}
</style>
