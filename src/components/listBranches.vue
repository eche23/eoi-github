<template>
  <ul id="branches">
    <li v-for="rama in branches" :key="rama.sha">
      <input @click="$emit('select-branch', rama.name)" v-model="branch" type="radio" :value="rama.name" :id="rama.sha">
      <label :for="rama.sha">{{rama.name}}</label>
    </li>
  </ul>
</template>

<script>

import axios from 'axios';

export default {
  name: 'listBranches',
  props: {
    branches: Array
  },
  data(){
    return{
      branch:''
    }
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
