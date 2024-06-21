<template>
  <div id="app">
    <!-- <AuthenticationComp/> -->
    <!-- <ProductsComp/> -->
    <!-- <BookComp/> -->
    <MortgageCalculator/>
    <BookComp/>
  </div>
</template>

<script>
// import AuthenticationComp from './components/AuthenticationComp.vue'
// import ProductsComp from './components/ProductsComp.vue'
// import BookComp from './components/BookComp.vue'
import MortgageCalculator from './components/MortgageCalculator.vue'

export default {
  name: 'App',
  components: {
    // AuthenticationComp,
    // ProductsComp
    // BookComp
    MortgageCalculator
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
