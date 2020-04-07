<template>
     <div class="col-md-4 col-sm-6 m-0">
        <div class="card border-info mt-5 ">
            <div class="card-header">              
                {{stock.name}}
                <small>(Price:{{stock.price}} | Quantity: {{stock.quantity}})</small>              
            </div>
            <div class="card-body mr-2">
              <div class="float-left">
                <input type="Number"
                        class="form-control"
                        placeholder="Quantity"
                        v-model="quantity"
                        :class= '{danger: insufficientQuantity}'
                       >
              </div>
              <div class="float-right ml-2">
                <button class="btn btn-info"
                        @click="sellStock"
                        :disabled="quantity <=0 || insufficientQuantity  ">{{insufficientQuantity ? 'Not enough ' : 'Sell' }}</button>
              </div>
            </div>
        </div>
      </div>  
</template>

<script>
import {mapActions} from 'vuex'
export default {
  props:['stock'],
  data(){
    return{
      quantity:0
    };
  },
  computed:{
    insufficientQuantity(){
      return this.quantity > this.stock.quantity;
    }
  },
  methods:{
    ...mapActions({
      placeSellOrder :'sellStock'
    }),
    sellStock(){
      const order = {
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: this.quantity
      };
      this.placeSellOrder(order);
      this.quantity = 0
    }
  }
}
</script>

<style scoped>
.danger{
  border:1px solid red;
}
</style>