<template>
  <div id="app">
    <calculator />
  </div>
</template>

<script>
import calculator from './components/Calculator.vue'

export default {
  name: 'App',
  components: {
    calculator
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
  margin-top: 60px;
}

@media (max-width: 768px) {
    #app {
      margin-top: 0px;
    }
}
</style>
