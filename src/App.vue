<template>
  <div id="app">

    <img alt="Vue logo" src="./assets/logo.png">
    <Commits msg="Welcome to Your Vue.js App"/>
    <Commit/>

  </div>
</template>

<script>


import Commit from './components/Commit.vue'
import Commits from './components/Commits.vue'


export default {
  name: 'app',
  components: {
    Commit,
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
