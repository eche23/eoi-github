<template>
  <div id="app">
    <input type="text" v-model="url" placeholder="Url" />
    <p v-if="error!=''">{{error}}</p>
    <h1 v-if="repo.user==''"></h1>
    <h1 v-else >Latest {{repo.name}} {{repo.user}} Commits</h1>
    <listBranches @select-branch="selectBranch" :branches="branches"/>
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
  data(){
    return{
      commits: [],
      branches: [],
      url: '',
      newUrl:'',
      error:'',
      repo: {
        user: '',
        name: '',
        branch: ''
      }
    }
  },
  watch:{
    'url'(){
      this.newUrl=this.url.replace('https://github.com/','https://api.github.com/repos/');

      this.branches=[];
      this.commits=[];
      
      if(!this.newUrl.includes('https://api.github.com/repos/')){
        this.error='Mira que esto no es de github';
        return;
      }
      
      this.repo.user = this.newUrl.split('/')[4];
      this.repo.name = this.newUrl.split('/')[5];
     
      axios.get(this.newUrl+'/branches')
      .then(response => {
        var lista = response.data.splice(0,5);
        lista.forEach(branch => {
          this.branches.push({name:branch.name,sha:branch.commit.sha});
        });
      })
      .catch(e => {
        this.repo= {
          user: '',
          name: '',
          branch: ''
        }
        this.error=e;
        console.log(e);
      });

    }
  },
  methods: {
    selectBranch(branch){
      
      this.repo.branch = branch;

      axios.get(this.newUrl+"/commits?sha="+branch)
      .then(res => {
        let list = res.data;
        list = list.slice(list.length-5);
        this.commits = list;
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
  display: flex;
  flex-direction: column;
}
</style>
