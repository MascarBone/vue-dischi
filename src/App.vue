<template>
  <div id="app">
    <Collection />
  </div>
</template>

<script>
import Collection from './components/Collection.vue'

export default {
  name: 'App',
  components: {
    Collection,
  }
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap-grid";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
