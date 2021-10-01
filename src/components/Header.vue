<template>
    <header>
        Io Sono Header
        <Searchbar />
    </header>
</template>

<script>
import Searchbar from './Searchbar.vue'

export default {
    name: 'Header',
    components: {
        Searchbar
    }
}
</script>


<style lang="scss" scoped>
header{
    width: 100%;
    height: 100px;
    background-color: aquamarine;
}
</style>
