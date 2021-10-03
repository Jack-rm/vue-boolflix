<template>
  <div id="app">
    <Wrapper msg="Welcome to my Boolflix!"/>
  </div>
</template>

<script>
import Wrapper from './components/Wrapper.vue';

export default {
  name: 'App',
  components: {
    Wrapper
  }
}
</script>

<style lang="scss">
@import 'style/general.scss';

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

</style>
