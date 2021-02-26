<template>
  <div class="container">
    <h1>Vista Proyectos</h1>
    <hr />
    <div class="row">
      <router-link
        to="/reg-projects"
        class="col s12 waves-effect waves-light btn"
      >
        <i class="material-icons">add</i>
        Crear Proyecto
      </router-link>
    </div>
    <Container />
  </div>
</template>

<script>
import Container from "../components/Container";
export default {
  components: {
    Container,
  },
};
</script>

<style></style>
