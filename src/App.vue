<template>
  <div id="app">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
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
  padding-top: 60px;
  background-color: transparent;
}
body{
  background-color: #E5E5F7;
background: radial-gradient(circle, transparent 20%, #E5E5F7 20%, #E5E5F7 80%, transparent 80%, transparent), radial-gradient(circle, transparent 20%, #E5E5F7 20%, #E5E5F7 80%, transparent 80%, transparent) 100px 100px, linear-gradient(#444CF7 8px, transparent 8px) 0 -4px, linear-gradient(90deg, #444CF7 8px, #E5E5F7 8px) -4px 0;
background-size: 200px 200px, 200px 200px, 100px 100px, 100px 100px;
}
</style>
