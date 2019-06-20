
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h3>Login</h3>
    <ul>
      <div>User: <input v-model="user" placeholder="Username"/></div>
      <div>Pass: <input v-model="pass" placeholder="Password"/></div>
      <button v-on:click="this.logon">Submit</button>
    </ul>
    <h3>Make Account</h3>
    <ul>
      <div>User <input v-model="makeuser" placeholder="Username"/></div>
      <div>Pass <input v-model="makepass" placeholder="Password"/></div>
      <div>Time <input v-model="maketime" placeholder="TimeSync (Second)"/></div>
      <button v-on:click="this.signup()">Submit</button>
    </ul>
    New User: <div>{{ this.makeuser }} | {{ this.makepass }} | {{ this.maketime }}</div>
    <div> Users: <div v-bind:key v-for="data in userjson">{{ data }}</div></div>
  </div>
</template>

<script>
import json from '../assets/users.json'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      userjson: json,
      user: null,
      pass: null,
      makeuser: null,
      makepass: null,
      maketime: null
    }
  },
  methods: {
    logon: function () {
      var i = 0
      var d = (new Date().getSeconds() % 10) 
      console.log(d)
      console.log(this.userjson.user)
      if (this.user == this.userjson[i].user){
        console.log('dank user found')
        if (this.userjson[i].time == d) {
          console.log('time match')
          if (this.userjson[i].pass == this.pass) {
            console.log("success!")
          } else {
            console.log("you're a f*king noob!")
          }
        } else {
          console.log('time sync error')
        }
      } else {
        console.log('no user')
      }
    },
    signup: function () {
      //need server up to be able to append to json file
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
