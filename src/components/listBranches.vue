<template>
  <ul id="branches">
    <li v-for="branch in branches" :key="branch.name">
      <input type="radio"><label>{{branch.name}}</label>
    </li>
  </ul>
</template>

<script>

import axios from 'axios';

export default {
  name: 'listBranches',
  data(){
    return {
      branches:[]
    }
  },
  created() {
    axios.get(`https://api.github.com/repos/python-telegram-bot/python-telegram-bot/branches`)
    .then(response => {
      response.data.forEach(branch => {
        this.branches.push(branch);
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
  text-decoration: none;
  
}
</style>
