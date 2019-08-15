<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>Latest repo user Commits</h1>
    <listBranches @select-branch="selectBranch" :url="url"/>
    <Commits :commits="commits" :repo="repo"/>
  </div>
</template>

<script>

import Commits from './components/Commits.vue'
import listBranches from './components/listBranches.vue'
import axios from 'axios'

export default {
  name: 'app',
  components: {
    Commits,
    listBranches
  },
  props:{

  },
  data(){
    return{
      commits: [],
      url: 'https://api.github.com/repos/python-telegram-bot/python-telegram-bot/',
      repo:{
        user: '',
        name: '',
        branch: ''
      }
    }
  },
  methods: {
    selectBranch(branch){

      console.log(branch);

      this.repo.branch = branch;
      this.repo.user = this.url.split('/')[4];
      this.repo.name = this.url.split('/')[5];

      axios.get(this.url+"commits?sha="+branch)
        .then(res => {
          
          let list = res.data;
          list = list.slice(list.length-5);
          this.commits = list;
          console.log(this.commits);
        })
        .catch(err => console.log(err));
    }
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
