<template>
  <div id="app">
    <Navbar/>
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue'

export default {
  name: 'App',
  components: {
    Navbar
  }
}
</script>

<style lang="scss">
html, body {
  background-color: $c-dark-900;
}
</style>
