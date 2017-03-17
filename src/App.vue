<template>
  <div id="app">
    <top-nav v-if="$store.getters.loggedIn"></top-nav>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app',
  components: {
    TopNav: require('./Nav')
  }
}
</script>

<style>
</style>
