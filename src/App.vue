<template>
  <div id="app">
    <a href="https://fontmeme.com/netflix-font/"><img src="https://fontmeme.com/permalink/211001/4937b74c6317b36c509baa13669b4b20.png" alt="netflix-font" border="0"></a>
    <HelloWorld msg="Welcome to my Boolflix!"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
