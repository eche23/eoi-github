<template>
  <div class="commits">
    <div v-for="commit in commits" :key="commit.sha">
        <div v-for="com in commit">
            <p>{{com.sha}}</p>
        </div>
            
        
    </div>
  </div>
</template>

<script>

import axios from 'axios'

export default {
  name: 'Commits',

  data: function() {
    return {
        commits: []
    }
  },

  created: function() {
    axios.get('https://api.github.com/repos/LuisJoseSanchez/aprende-java-con-ejercicios/commits?sha=master')
    .then(response => {
      this.commits.push(response.data);
    })
  }
}
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
