<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{ users }}</h2>
    
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data: function () {
    return {
      users: {}
    }
  },
  created () {
    axios.get('https://randomuser.me/api/?page=1&results=1&seed=abc&inc=gender,name,nat,phone,picture&nat=us')
      .then(response => {
        console.log(response)
        this.users = response.data
      })
      .catch(err => {
        console.log(err)
      })
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
