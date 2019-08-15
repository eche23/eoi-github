<template>
  <div id="app">
    <h1>Lastest repo user Commits</h1>
    <listBranches/>
  </div>
</template>

<script>

import listBranches from './components/listBranches.vue';

export default {
  name: 'app',
  components: {
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
