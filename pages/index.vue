<template lang="html">
  <div class="container">
    <h1 class="title is-2 Title-photo has-text-centered">Fotografos</h1>
      <div class="columns is-multiline is-centered">
        <div class="column is-6" v-for="user in users" :key="user.id">
          <BoxProfile :photographer="user"/>
        </div>
      </div>
  </div>
</template>

<script>
  import axios from 'axios';
  import env from '../config/env.js';
  import BoxProfile from '../components/BoxProfile';
  export default {
    name: 'IndexPage',
    layout: 'navbar',
    components:{
      BoxProfile
    },
    async asyncData({ params }) {
      let _users = (await axios.get(`${env.endpoint}/users`)).data;
      return { users: _users };
    }
  };
</script>

<style>
  .Title-photo{
    margin-bottom: 30px !important;
  }
</style>


