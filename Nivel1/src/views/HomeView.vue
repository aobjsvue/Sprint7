<template>
  <div>
    <Home />
    <router-link to="/">
      <button type="button">Tornar enrere</button>
    </router-link>
  </div>
</template>

<script>
// @ is an alias to /src
import Home from '@/components/Home.vue'

export default {
  name: 'HomeView',
  components: {
    Home
  }
}
</script>

<style>
  button {
    margin-top: 0.7em;
  }
</style>
