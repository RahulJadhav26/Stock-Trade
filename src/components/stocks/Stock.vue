<template>
     <div class="col-md-4 col-sm-6 m-0">
        <div class="card border-success mt-5 ">
            <div class="card-header">              
                {{stock.name}}
                <small>(Price:{{stock.price}})</small>              
            </div>
            <div class="card-body mr-2">
              <div class="float-left">
                <input type="Number"
                        class="form-control"
                        placeholder="Quantity"
                        v-model="quantity"
                        :class= '{danger: insufficientFunds}'
                       >
              </div>
              <div class="float-right ml-2">
                <button class="btn btn-success"
                        @click="buyStock"
                        :disabled="insufficientFunds || quantity<=0">{{ insufficientFunds ? 'Less Funds' : 'Buy'}}</button>
              </div>
            </div>
        </div>
      </div>  
</template>

<script>
export default {
  props:['stock'],
  data(){
    return{
      quantity:0
    };
  },
  computed:{
    funds(){
      return this.$store.getters.funds;
    },
    insufficientFunds(){
      return this.quantity * this.stock.price > this.funds;
    }
  },
  methods:{
    buyStock(){
      const order ={
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: this.quantity,

      };
      console.log(order);
      this.$store.dispatch('buyStock',order)
      this.quantity = 0;
    }
  }
}
</script>

<style scoped>
.danger{
  border:1px solid red;
}
</style>