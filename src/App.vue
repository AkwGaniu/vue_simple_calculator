<template>
  <div id="app">
    <calculator />
    <appFooter />
  </div>
</template>

<script>
import calculator from './components/Calculator.vue'
import appFooter from './components/appFooter.vue'
export default {
  name: 'App',
  components: {
    calculator,
    appFooter
  }
}
</script>

<style>
body {
  margin: 0
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 0px;
}

@media (max-width: 768px) {
    #app {
      margin-top: 0px;
    }
}
</style>
