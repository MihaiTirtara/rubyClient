<template>
  <div id="app">
    <company-dashboard></company-dashboard>
  </div>
</template>

<script>
import CompanyDashboard from './components/CompanyDashboard.vue'
export default {
  name: 'app',
  components: {
    CompanyDashboard
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
