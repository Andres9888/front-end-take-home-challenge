<template>
  <div class="hello">
    <div class="container">
      <input class="searchBar" type="text" v-model="searchQuery" placeholder="Search">
    <form @submit.prevent="submit">
       <input type="text" v-model="firstname" placeholder="First Name"> 
       <input type="text" v-model="phone" placeholder="Phone Number"> 
       <button type="submit">
         Add New User
       </button>
    </form>
  <div class="card" v-for="(user, index) in filteredUsers" :key="user">
    <img :src="`${user.picture.large}`">
    <h2>
    {{ user.name.first}}
  </h2>
    <i class="fas fa-arrow-right"></i>
    <p>{{ user.phone}}</p>
    <div class="pic"></div>
    <ul>
      <li></li>
    </ul>
    <button v-on:click="removeEntry(index)">x
    </button>
  </div>
  </div>
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
      searchQuery:'',
      firstname:'', 
      phone:'',
      users: {},
      
    }
  },
  created () {
    axios.get('https://randomuser.me/api/?page=1&results=10&seed=abc&inc=gender,name,nat,phone,picture&nat=us')
      .then(response => {
        console.log(response)
        this.users = response.data.results
      })
      .catch(err => {
        console.log(err)
      })
  },
  computed: {
    filteredUsers: function(){
      if(this.searchQuery){
      return this.users.filter((item)=>{
        return this.searchQuery.toLowerCase().split('').every(v => item.name.first.toLowerCase().includes(v) || item.phone.toLowerCase().includes(v))
      })
      }else{
        return this.users;
      }
    }
  
  },
  methods : {
      
      submit(){
          var user = {"gender":"female","name":{"title":"Miss","first":this.firstname,"last":"Woods"},"phone":this.phone,"picture":{"large":"https://randomuser.me/api/portraits/women/88.jpg","medium":"https://randomuser.me/api/portraits/med/women/88.jpg","thumbnail":"https://randomuser.me/api/portraits/thumb/women/88.jpg"},"nat":"US"}
            this.users.push(user);
      },
      removeEntry:function(index) {
        this.users.splice(index, 1)
      }
 
}}
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
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

i {
  opacity: 0;
  font-size: 18px;
  color: #fff;
  will-change: transform;
  -webkit-transform: scale(0.1);
  transform: scale(0.1);
  -webkit-transition: all 0.2s ease;
  transition: all 0.2s ease;
}

h2 {
  pointer-events: none;
}

body {
  background-color: #e6e5e1;
  width: 100vw;
  height: 100vh;
}
img{border-radius:50%;
  box-shadow: 0 19px 38px rgba(0,0,0,0.30), 0 15px 12px rgba(0,0,0,0.22);
}
input{
  margin-bottom:10px;
  width:500px;
  height: 48px;
  -webkit-box-align: center ;
    -ms-flex-align: center ;
    -webkit-align-items: center ;
    align-items: center ;
    background-color: #FFFFFF ;
    border: 1px solid #DDDDDD ;
    border-radius: 24px ;
    color: #222222 ;
    display: inline-flex ;
    max-width: 100% ;
    text-align: left ;
    transition: box-shadow 0.2s ease ;
    vertical-align: middle ;
    align-items: center ;
    background-color: #FFFFFF ;
    border: 1px solid #DDDDDD ;
    border-radius: 24px ;
    color: #222222 ;
    display: inline-flex ;
    max-width: 100% ;
    text-align: left ;
    transition: box-shadow 0.2s ease ;
}
.container {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.container .searchBar {
  margin-bottom:10px;
  width:500px;
  height: 48px;
  -webkit-box-align: center ;
    -ms-flex-align: center ;
    -webkit-align-items: center ;
    align-items: center ;
    background-color: #FFFFFF ;
    border: 1px solid #DDDDDD ;
    border-radius: 24px ;
    color: #222222 ;
    display: inline-flex ;
    max-width: 100% ;
    text-align: left ;
    transition: box-shadow 0.2s ease ;
    vertical-align: middle ;
    align-items: center ;
    background-color: #FFFFFF ;
    border: 1px solid #DDDDDD ;
    border-radius: 24px ;
    color: #222222 ;
    display: inline-flex ;
    max-width: 100% ;
    text-align: left ;
    transition: box-shadow 0.2s ease ;
}
.container .card {
  position: relative;
  width: 500px;
  height: 200px;
  background-color: #fff;
  overflow: hidden;
  margin-bottom: 4px;
  border-radius:5%;
  box-shadow: 0 19px 38px rgba(0,0,0,0.30), 0 15px 12px rgba(0,0,0,0.22);
}
.container .card:before {
  content: "";
  z-index: 99;
  position: absolute;
  top: -10px;
  left: 32px;
  display: block;
  width: 16px;
  height: 16px;
  border-radius: 16px;
  background-color: #e6e5e1;
}
.container .card:after {
  content: "";
  z-index: 99;
  position: absolute;
  bottom: -10px;
  left: 32px;
  display: block;
  width: 16px;
  height: 16px;
  border-radius: 16px;
  background-color: #e6e5e1;
}
.container .card ul {
  z-index: 99;
  position: absolute;
  left: 39px;
  top: 5px;
  list-style-type: none;
}
.container .card ul li {
  width: 2px;
  height: 2px;
  border-radius: 2px;
  margin: 6px 0;
  background-color: #e6e5e1;
}
.container .card h2 {
  z-index: 99;
  font-family: "Poppins", sans-serif;
  position: absolute;
  bottom: 0;
  right: 130px;
  font-size: 60px;
  font-weight: 700;
  color: #fff;
}
.container .card .fa-arrow-right {
  z-index: 100;
  position: absolute;
  right: 75px;
  bottom: 25px;
  font-size: 40px;
  cursor: pointer;
}
.container .card p {
  z-index: 99;
  position: absolute;
  top: 20px;
  right: 70px;
  color: #333;
  opacity: 0.7;
  font-size: 12px;
  letter-spacing: 1px;
  writing-mode: vertical-lr;
  -webkit-transition: all 0.2s ease;
  transition: all 0.2s ease;
}
.container .card .pic {
  z-index: 100;
  width: 400px;
  height: 200px;
  background-color: gray;
  background-size: 100% 100%;
  filter: grayscale(100%);
}
.container .card:hover i {
  opacity: 1;
  -webkit-transform: scale(1);
  transform: scale(1);
}
.container .card button {
  position: absolute;
  right: 14px;
  bottom: 14px;
  width: 30px;
  height: 30px;
  background-color: #da4d1d;
  border: none;
  border-radius: 30px;
  cursor: pointer;
  outline: none;
  transition: all 0.3s ease;
  mix-blend-mode: hard-light;
}
.container .card button i {
  font-size: 3rem;
}
.container .card:hover button {
  transform: scale(16.5);
}
.container .card:hover p {
  color: #fff;
}
.container .card:hover .pic {
  filter: grayscale(0);
}
.container .card2 .pic {
  background-image: url("https://images.unsplash.com/photo-1528785198459-ec50485704c7?ixlib=rb-0.3.5&s=3a2fc3039516555bbb2e9cd2967bd321&auto=format&fit=crop&w=1537&q=80");
}
.container .card2 button {
  background-color: #2b26c3;
}

.dr {
  position: absolute;
  bottom: 16px;
  right: 16px;
  width: 100px;
}
</style>
