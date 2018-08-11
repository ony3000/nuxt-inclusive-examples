<template>
  <div class="container">
    <h1>Hello world!</h1>
    <p>
      <button class="button is-medium is-primary hvr-float-shadow" @click="showNotify">Notify me!</button>
    </p>
    <p>
      <nuxt-link to="/about">About page</nuxt-link>
    </p>

    <h2>Users</h2>
    <ul class="users">
      <li v-for="user in users" :key="user.id">
        <nuxt-link :to="'/users/'+user.id">{{ user.name }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

let miniToastr
if (process.browser) {
  miniToastr = require('mini-toastr').default;
}

export default {
  async asyncData() {
    const { data } = await axios.get('https://jsonplaceholder.typicode.com/users');
    return { users: data };
  },
  head: {
    title: 'Inclusive Examples',
  },
  mounted() {
    miniToastr.init();
  },
  notifications: {
    showNotify: {
      title: 'Welcome!',
      message: 'Hello from nuxt.js',
      type: 'info',
    },
  },
};
</script>

<style scoped>
.users {
  list-style-type: none;
  padding: 0;
}
.users li a {
  display: inline-block;
  width: 200px;
  border: 1px #ddd solid;
  padding: 10px;
  text-align: left;
  color: #222;
  text-decoration: none;
}
.users li a:hover {
  color: orange;
}
</style>
