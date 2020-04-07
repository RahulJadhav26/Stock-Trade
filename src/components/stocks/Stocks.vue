<template>
  <div>
    <div class="row">
    <app-Stock v-for="stock in stocks" :key="stock.id" :stock="stock"></app-Stock>
  </div>
   </div>    
</template>

<script>
import StockVue from './Stock.vue';

export default {    
    components:{
      appStock:StockVue
    },
    computed:{
      stocks(){
        return this.$store.getters.stocks;
      }
    }
}
</script>

<style>

</style>