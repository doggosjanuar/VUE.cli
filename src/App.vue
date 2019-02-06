<template>
  <div id="app">
    <Tugas/>
  </div>
</template>

<script>

import 'bootstrap-vue/dist/bootstrap-vue.css'
import 'bootstrap/dist/css/bootstrap.css'
import Tugas from "./components/Tugas";

export default {
  name: 'app',
  components: {
      Tugas,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #1a564b;
  margin-top: 60px;
}
</style>
