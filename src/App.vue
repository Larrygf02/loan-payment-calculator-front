<template>
  <Simulate msg="Welcome to Your Vue.js App"/>
</template>

<script>
import Simulate from './components/Simulate.vue'

export default {
  name: 'App',
  components: {
    Simulate
  }
}
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
  background: #fec107;
  padding: 0 10px;
}
</style>
