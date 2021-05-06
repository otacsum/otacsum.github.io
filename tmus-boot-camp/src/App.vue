<template>
  <div id="app">
    <div class="app-header">
      <a href="index.html">
        <img alt="T-Mobile P&T Bootcamp" title="T-Mobile P&T Bootcamp" src="./assets/tmo-logo-v3.svg" />
      </a>
    </div>
    <calculator msg="Welcome to Mike's Calculator"/>
  </div>
</template>

<script>
import calculator from './components/calculator.vue'

export default {
  name: 'App',
  components: {
    calculator
  }
}
</script>
