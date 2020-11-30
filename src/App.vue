<template>
  <div id="app">
    <div class="container">
        <h1><b>Github</b> <i>Search</i></h1>
        <div class="card card-body header">
            <input v-on:keyup.enter="getUser" v-model="userName" id="search-bar" type="text" class="form-control" required/>
            <button @click="getUser" class="btn btn-dark"><i class="fa fa-search fa-2x" aria-hidden="true"></i></button>
        </div>
        <div class="row mt-3" v-if="user.length !== 0">
            <div class="col-md-4">
                <Profile :user="user"/>
            </div>
            <div class="col-md-8">
                <Repo v-for="repo in repos" :key="repo" :repo="repo"/>
            </div>
        </div>
    </div>
  </div>
</template>

<script>

import Profile from './components/Profile.vue';
import Repo from './components/Repo.vue';
import axios from "axios";

export default {
  name: 'App',
  data() {
      return {
          github: {
              url: 'https://api.github.com/users',
              count: 7,
              client_id: '3a12789ec41d033a36d4',
              client_secret: '4ad7e8f0461184467be54b06cf9b0b01811ec2e7',
              sort: "created: asc"
          },
          user: [],
          repos: [],
          userName: ""
      };
  },
  components: {
      Profile,
      Repo
  },
  methods: {
      getUser(){
        const user = this.userName;
        const { url, client_id, client_secret, count, sort } = this.github;
        axios
            .get(
                `${url}/${user}?client_id=${client_id}&client_secret=${client_secret}`
            )
            .then(({ data }) => (this.user = data))
            .catch(error => alert('User not found'));
        axios
            .get(
                `${url}/${user}/repos?per-page=${count}&sort=&{sort}&client_id=${client_id}&client_secret=${client_secret}`
            )
            .then(({ data}) => this.repos = data);
    }
  }
}
</script>