<template>
  <v-toolbar dark class="light-green darken-4">
    <v-toolbar-title class="white--text">
        <span class ="logo" @click="navigateTo({ name: 'songs'})" flat>Guit Strings</span>
    </v-toolbar-title>
    <v-toolbar-items class="pl-3">
    </v-toolbar-items>
    <v-spacer></v-spacer>
      <v-toolbar-items>
        <v-btn flat @click="navigateTo({name:'songs'})">
          Browse
        </v-btn>
        <v-btn v-if=" !$store.state.isUserLoggedIn " flat @click="navigateTo({ name: 'login'})">
          Login
        </v-btn>
        <v-btn v-if=" $store.state.isUserLoggedIn " flat @click="logout">
          Log Out
        </v-btn>
        <v-btn v-if=" !$store.state.isUserLoggedIn " flat @click="navigateTo({ name: 'register'})">
          Sign Up
        </v-btn>
      </v-toolbar-items>
  </v-toolbar>
</template>
<script>
export default {
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    },
    logout () {
      this.$store.dispatch('setToken', null)
      this.$store.dispatch('setUser', null)
      this.$router.push({
        name: 'songs'
      })
    }
  }
}
</script>
<style scoped>
.logo {
  cursor:pointer;
  font-weight: bold;
}
.refresh:hover
{
  opacity: 0.8;
}
</style>
