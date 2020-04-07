<template>
    <div class="container">
        <app-Header></app-Header>
         <router-view></router-view>        
    </div> 
</template>

<script>
import HeaderVue from './components/Header.vue'

    export default {
        components:{
            appHeader:HeaderVue
        },
        created(){
            this.$store.dispatch('initStocks');
        }
    }
</script>

<style>
body{
    padding: 30px;
}
</style>
