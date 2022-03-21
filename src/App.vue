<template>
  <div id="app">
    <ServerInfo/>
  </div>
</template>

<script>
import ServerInfo from './components/ServerInfo.vue'

export default {
  name: 'App',
  components: {
    ServerInfo
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
