<template>
  <!-- <HelloWorld/> -->
  <Users></Users>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Users from './components/Users.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    Users
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
