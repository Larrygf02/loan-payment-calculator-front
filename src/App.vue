<template>
  <Simulate msg="Welcome to Your Vue.js App"/>
</template>

<script>
import Simulate from './components/Simulate.vue'
// import Vue from 'vue';
export default {
  name: 'App',
  components: {
    Simulate
  }
}
/* new Vue({
  components: {
    Simulate
  }
}); */
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@100&display=swap');
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Montserrat', sans-serif;
}

#app {
  /*background: #009d9a;*//*98ff96*/
  padding: 0 10px;
}
</style>
