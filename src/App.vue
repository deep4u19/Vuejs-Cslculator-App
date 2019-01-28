<template>
  <div id="app">
    <app-header></app-header>
    <calculator></calculator>
    
  </div>
</template>

<script>
import calc from './Components/calculator.vue'
import appHeader from './Components/header.vue'
export default {
  components:{
    'calculator':calc,
    'app-header':appHeader
  }
  
}
</script>

<style scoped>

</style>
