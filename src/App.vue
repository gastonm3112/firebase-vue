<template>
  <div id="nav">
    <Navbar />
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
    <router-view />
  </div>
</template>

<script>
//@ es un atajo a la carpeta componets
import Navbar from "@/components/Navbar.vue";

export default {
  components: {
    Navbar,
  },
};
</script>
