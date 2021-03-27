<template>
  <div class="navbar">
    <nav>
      <div class="nav-wrapper cyan darken-1">
        <router-link v-if="sesion" class="brand-logo" to="/"
          >Proyectos</router-link
        >
        <a href="#" data-target="mobile-demo" class="sidenav-trigger"
          ><i class="material-icons">menu</i></a
        >
        <ul class="right hide-on-med-and-down">
          <li>
            <router-link v-if="!sesion" to="/">Sign Up</router-link>
          </li>
          <li>
            <router-link
              v-if="!sesion"
              class="btn waves-effect waves-green transparent"
              to="/login"
              >Sign In</router-link
            >
          </li>
          <li>
            <router-link
              v-if="sesion"
              class="waves-effect waves-light btn red accent-2"
              to="/proyectos"
              >Proyectos</router-link
            >
          </li>
          <li>
            <router-link
              v-if="sesion"
              class="waves-effect waves-light btn red accent-2"
              to="/"
              @click="cerrarSesion"
              >Sign out</router-link
            >
          </li>
        </ul>
      </div>
    </nav>

    <ul class="sidenav" id="mobile-demo">
      <li>
        <router-link v-if="!sesion" to="/">Sign Up</router-link>
      </li>
      <li>
        <router-link v-if="!sesion" to="/login">Sign In</router-link>
      </li>
      <li>
        <router-link to="/proyectos">Proyectos</router-link>
      </li>
      <li>
        <router-link
          v-if="sesion"
          class="waves-effect waves-light btn red accent-2"
          to="/"
          @click="cerrarSesion"
          >Sign out</router-link
        >
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: () => ({
    user: false,
  }),
  mounted() {
    M.AutoInit();
  },
  methods: {
    cerrarSesion() {
      localStorage.removeItem("user");
    },
  },
  computed: {
    sesion() {
      const user = localStorage.getItem("user");

      if (user) {
        return true;
      }

      return false;
    },
  },
};
</script>

<style></style>
