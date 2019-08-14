<template>
  <div id="app">
    <Commits msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import Commits from './components/Commits.vue'

export default {
  name: 'app',
  components: {
    Commits
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
