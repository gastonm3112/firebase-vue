<template>
  <div id="nav">
    <Navbar />

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
