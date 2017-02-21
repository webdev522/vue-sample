<template>
  <div id="app">
    <users></users>
    <!--<test msg="hello"></test>-->
  </div>
</template>

<script>

import Test from './components/test'
import Users from './components/users'

export default {
  name: 'app',
  components: {
    Users, Test
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
