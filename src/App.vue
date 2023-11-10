<script>
import { RouterView } from 'vue-router';
import Navbar from './components/Navbar.vue'
import HomePage from './pages/HomePage.vue';


export default {
  components: { Navbar, HomePage },
};
</script>

<template>
  <Navbar />
  <div class="container">
      <RouterView />
  </div>
</template>

<style lang="scss" scoped></style>