<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <ul>
    <li v-for="(person, index) in users" :key="index">
      {{person.name + " " + person.surname}}
    </li>
  </ul>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import axios from 'axios'

export default {
  name: 'App',
  data () {
    return {
      users: null
    }
  },
  components: {
    HelloWorld
  },
  mounted() {
    //axios.defaults.headers.common['Access-Control-Allow-Origin'] = '*';
    axios.get('https://ipi-express-demo.herokuapp.com/users')
    .then(response => this.users = response.data)
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
