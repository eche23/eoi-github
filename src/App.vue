<template>
  <div id="app">

    <img alt="Vue logo" src="./assets/logo.png">
    <Commits msg="Welcome to Your Vue.js App"/>
    <Commit/>

    <h1>Lastest repo user Commits</h1>
    <listBranches/>
  </div>
</template>

<script>


import Commit from './components/Commit.vue'
import Commits from './components/Commits.vue'
import listBranches from './components/listBranches.vue';

export default {
  name: 'app',
  components: {
    Commit,
    Commits,
    listBranches
  }
}

</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 3rem;
}
</style>
