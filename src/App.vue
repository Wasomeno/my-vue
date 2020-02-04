<template>
  <div id="app">
    <Practice1 />
  </div>
</template>

<script>
import Practice1 from './components/Practice1.vue'

export default {
  name: 'app',
  components: {
    Practice1
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
