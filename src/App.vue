<template>
  <div id="app">
    <hello></hello>
    <carousel></carousel>
  </div>
</template>

<script>
import Hello from './components/Hello'
import Carousel from './components/Carousel'

export default {
  name: 'app',
  components: {
    Hello,
    Carousel
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 30px;
  
}
</style>
