<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-link to="/login">登录</router-link>
    <router-view></router-view>
  </div>
</template>

<script>

export default {
  name: 'app'
}
</script>

<style>
body{
  background-color: #2b4b6b;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #e6ebf0;
  margin-top: 60px;
}
</style>
