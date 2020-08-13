<template>
  <div id="app">
    <simple-shuffle></simple-shuffle>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import simpleShuffle from '@/components/simple_shuffle.vue'
export default {
  name: 'App',
  components: {
    'simple-shuffle': simpleShuffle
  }
}
</script>

<style>

body{
    position: absolute;
    width: 100%;
    height: 100%;
    left: 0;
    top: 0;
    margin: 0 !important;
    background: #101010;
    padding: 0;
    user-select: none;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
