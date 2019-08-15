<template>
  <ul id="branches">
    <li v-for="rama in branches" :key="rama.sha">
      <input @click="viewBranch(rama.name)" v-model="branch" type="radio" :value="rama.name" :id="rama.sha">
      <label :for="rama.sha">{{rama.name}}</label>
    </li>
  </ul>
</template>

<script>

import axios from 'axios';

export default {
  name: 'listBranches',
  data(){
    return {
      branch:"",
      branches:[]
    }
  },
  methods:{
    viewBranch(valor){
      this.branch = valor;
    }
  },
  created() {
    axios.get(`https://api.github.com/repos/python-telegram-bot/python-telegram-bot/branches`)
    .then(response => {
      var lista =response.data;

      lista=lista.slice(lista.length-5);

      lista.forEach(branch => {
        this.branches.push({name:branch.name,sha:branch.commit.sha});
      });

    })
    .catch(e => {
        this.branches.push(e);
    })
  }

}

</script>

<style scoped>
#branches{
  display: flex;
  list-style: none;
}

#branches li{
    flex-grow: 1;
}

</style>
