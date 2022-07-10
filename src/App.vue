<template>
  <div id="app">
   <p>Ola mundo</p>
   <root></root>
  </div>
</template>

<script>
//import FormApp from './components/FormApp.vue'
import root from './components/root.vue'

export default {
  name: 'App',
  components:{
    root
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
