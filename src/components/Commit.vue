<template>
  <div class="commit">
    
    <p>
      <a :href="commit.html_url" class="link">{{commit.committer.id}}</a> {{commit.commit.message}} <br>
      by: <a :href="commit.author.html_url">{{commit.commit.author.name}}</a> at {{commit.commit.committer.date}} 
    </p>

    
  </div>
</template>

<script>
export default {
  name: 'Commit',
  props: {
    commit: Object
  },
  data(){
    return{
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
