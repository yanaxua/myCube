<template>
  <div id="app">
    <router-link to="/">HelloWorld1</router-link>
    <router-link to="/HelloWorld2">HelloWorld2</router-link>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style>
html,body{
  width: 100%;
  height: 100%;
}
*{
  padding: 0;
  margin: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 100%;
  height: 100%;
}
</style>
