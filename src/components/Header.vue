<template>
  <div class="container">
      <nav class="navbar navbar-expand-lg navbar-light bg-light">
  <router-link to="/" tag="a" class="navbar-brand">Stock Trader</router-link>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>

  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav mr-auto">
      <router-link to="/portfolio" class="nav-item"  tag="li"><a class="nav-link">
      PortFolio<span class="sr-only">(current)</span>
      </a></router-link>
      <router-link to="/stocks" class="nav-item"  tag="li"><a class="nav-link">
      Stocks<span class="sr-only">(current)</span>
      </a></router-link>              
    </ul>
  
    <ul class="navbar-nav ml-auto">
      <router-link to="#" class="nav-item "  tag="li"><a class="nav-link">
      End day<span class="sr-only">(current)</span>
      </a></router-link>
      <router-link to="#" class="nav-item "  tag="li"><a class="nav-link">
       Save &  Load<span class="sr-only">(current)</span>
      </a></router-link>
      <strong class="nav-text mt-2 ml-2 ">Funds :{{funds | currency}}</strong>
    </ul>
  </div>
</nav>
  </div>
</template>

<script>
export default {
  computed:{
    funds(){
      return this.$store.getters.funds;
    }
  }
}
</script>

<style>

</style>