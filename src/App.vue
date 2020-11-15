<template>
<b-container fluid>
  <b-row class="my-3">
    <div id="app">
    <b-form-input v-model="text" placeholder="Enter your name">Input Name</b-form-input>
    <b-button variant="danger"> Submit</b-button>
   <button class="btn btn-danger" @click="getDataDb">{{test}}</button>
  </div>
  <div>
    <table class="table">
      <thead>
        <tr>
          <th>Nama</th>
          <th>Email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" v-bind:key="user.id">
          <td>{{ user.name }}</td>
          <td>{{ user.email }}</td>
        </tr>
      </tbody>
    </table>
  </div>
  </b-row>
</b-container>
  
</template>


<script>
import axios from "axios"

export default {
  name: 'App',
  data: function() {
    return {
      test: "Hendra Arya",
      users: []
    }
  },
  methods: {
    async getDataDb() {
      let response = await axios.get("http://localhost:8000/api/hendra"); //untuk connect ke Backend Laravel menggunakan API yang telah dicreate di dalam Laravel
      let data = response.data;
      this.users = data;
      console.log(data);
    }
  },
  components: {
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
