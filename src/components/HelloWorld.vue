<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{ pokemon }}</h2>
    
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
      pokemon: {}
    }
  },
  created () {
    axios.get('https://pokeapi.co/api/v2/pokedex/kanto/')
      .then(response => {
        console.log(response)
        this.pokemon = response.data
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
