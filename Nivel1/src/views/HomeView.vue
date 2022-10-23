<template>
  <div>
    <Home />
  </div>
  <router-link to="/">
    <button type="button">Tornar enrere</button>
  </router-link>
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
