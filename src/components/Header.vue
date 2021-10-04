<template>
    <header>
        <div class="container">
            <div class="row justify-content-between align-items-center">
                <div class="col-4">
                    <Logo />
                </div>
                <div class="col-5">
                    <!-- RECEIVE -needle- from Searchbar -->
                    <Searchbar @send="receive" />
                </div>
            </div>
        </div>
    </header>
</template>

<script>
import Searchbar from './Searchbar.vue'
import Logo from './Logo.vue'

export default {
    name: 'Header',

    components: {
    Searchbar,
    Logo    
    },

    data : function(){
        return{
        }
    },

    methods : {
        receive(needle){
            // Check
            console.clear()
            console.log('Header needle:', needle)
            // SEND -needle- to App 
            this.$emit('send', needle)
        }
    }
}
</script>

<style lang="scss" scoped>
@import '../style/general.scss';
@import '../style/variables.scss';

header{
    background-color: $background;
    margin-bottom: 20px;
}
</style>