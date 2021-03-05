<template>
  <div class="navbar">
    <nav>
      <div class="nav-wrapper cyan darken-1">
        <router-link class="brand-logo" to="/">Proyectos</router-link>
        <a href="#" data-target="mobile-demo" class="sidenav-trigger"
          ><i class="material-icons">menu</i></a
        >
        <ul class="right hide-on-med-and-down">
          <li>
            <router-link to="/">Sign Up</router-link>
          </li>
          <li>
            <router-link
              class="btn waves-effect waves-green transparent"
              to="/login"
              >Sign In</router-link
            >
          </li>
          <li>
            <router-link
              class="waves-effect waves-light btn red accent-2"
              to="/proyectos"
              >Proyectos</router-link
            >
          </li>
        </ul>
      </div>
    </nav>

    <ul class="sidenav" id="mobile-demo">
      <li>
        <router-link to="/">Sign Up</router-link>
      </li>
      <li>
        <router-link to="/login">Sign In</router-link>
      </li>
      <li>
        <router-link to="/proyectos">Proyectos</router-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  mounted() {
    M.AutoInit();
  },
};
</script>

<style></style>
