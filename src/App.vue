<template>
  <div id="app">
    <img src="./assets/lcl.jpg" alt="logo lcl" width="400" height="150">
    <BankManager msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import BankManager from './components/BankManager.vue'

export default {
  name: 'app',
  components: {
    BankManager
  }
}
</script>

<style lang="scss">
 @import "./assets/custom.scss";
 @import "../node_modules/bootstrap/scss/bootstrap.scss";

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

img {
  margin: 20px 0;
}
</style>
