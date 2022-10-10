<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <CardComponent />
  </div>
</template>

<script>
import CardComponent from './components/CardComponent.vue';
export default {
  name: 'App',
  components: {
    CardComponent
}
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Work+Sans&display=swap');
  #app {
    font-family: 'Work Sans', sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: white;
    margin-top: 60px;
  }
  </style>
