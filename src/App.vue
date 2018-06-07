<template>
  <div id="app">
    <div class="row">
      <top-nav-bar></top-nav-bar>
    </div>
     <div class="container">
       <div class="row">
         <app-cards></app-cards>
       </div>
     </div>
  </div>
</template>

<script>
  import TopNavBar from './components/TopNavBar.vue';
  import AppCards from './components/AppCards.vue';
export default {
    components : {
      TopNavBar,
      AppCards
    }
  }
</script>

<style>
  #app{
    background-color: darkgrey;
  }
</style>
