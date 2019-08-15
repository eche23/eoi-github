<template>
  <div class="commits">
    <h2 v-if="repo.user!=''">{{repo.user}}/{{repo.name}}@{{repo.branch}}</h2>
    <div v-for="commit in commits" :key="commit.sha">

      <Commit :commit="commit"/>

            
        
    </div>


  </div>
</template>

<script>

import Commit from './Commit.vue'

export default {
  name: 'Commits',
  props:{
    commits: Array,
    repo: Object
  },
  components:{
    Commit
  },
  data: function() {
    return {
        /* commits: [] */
    }
  },

/*   created: function() {
    axios.get('https://api.github.com/repos/LuisJoseSanchez/aprende-java-con-ejercicios/commits?sha=master')
    .then(response => {
      this.commits.push(response.data);
    })
  } */
}
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
