<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <users-component :users = 'users' @onDelete = "onDelete"></users-component>
    <!-- <button @click="getUsers">Click</button> -->
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import axios from 'axios'
import UsersComponent from './components/UsersComponent.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    UsersComponent
  },
  data(){
    return{
      url: "https://jsonplaceholder.typicode.com/users",
      users:[]
    }
  },
  methods:{
    getUsers(){
      axios.get(this.url)
      .then(data=>{
        // console.log(data.data[0])
        this.users = data.data;
      })
    },
    deleteUser(id){
      axios.delete(`${this.url}/${id}`.then(()=>{
        this.getUsers();
      }))
      .catch(err=>{
        console.log(err);
      })
    },
    onDelete(id){
      // console.log('Deleting from App vue', id)
      this.deleteUser(id)
    }
  },
  created(){
    this.getUsers();
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
