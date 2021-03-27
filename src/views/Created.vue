<template>
  <div class="container">
    <div class="row">
      <router-link
        to="/proyectos"
        class="col s12 waves-effect waves-light btn light-blue accent-3"
      >
        <i class="material-icons">arrow_back</i>
        Regresar a Vista de Proyectos
      </router-link>
    </div>
    <div class="row">
      <form @submit.prevent="registrarProyecto" class="col s12">
        <div class="row">
          <div class="input-field col s12">
            <input
              id="project_name"
              type="text"
              class="validate"
              v-model="project.title"
            />
            <label for="project_name">Nombre del Proyecto</label>
          </div>
          <div class="input-field col s12">
            <input
              id="project_description"
              type="text"
              class="validate"
              v-model="project.description"
            />
            <label for="project_description">Descripción del Proyecto</label>
          </div>
          <p>
            <label>
              <input type="checkbox" v-model="project.langs" value="Html" />
              <span>HTML</span>
            </label>
          </p>
          <p>
            <label>
              <input type="checkbox" v-model="project.langs" value="Css" />
              <span>CSS</span>
            </label>
          </p>
          <p>
            <label>
              <input
                type="checkbox"
                v-model="project.langs"
                value="JavaScript"
              />
              <span>JavaScript</span>
            </label>
          </p>
          <p>
            <label>
              <input type="checkbox" v-model="project.langs" value="Vue" />
              <span>Vue</span>
            </label>
          </p>
          <p>
            <label>
              <input type="checkbox" v-model="project.langs" value="React" />
              <span>React</span>
            </label>
          </p>
          <button
            class="btn waves-effect waves-light col s12"
            type="submit"
            name="action"
          >
            Submit
            <i class="material-icons right">send</i>
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    project: {
      title: "",
      description: "",
      langs: [],
      status: true,
    },
  }),
  methods: {
    async registrarProyecto() {
      const user = JSON.parse(localStorage.getItem("user"));
      await fetch(
        `https://crud-en-vue3-default-rtdb.firebaseio.com/projects/${user.localId}.json?auth=${user.idToken}`,
        {
          method: "POST",
          body: JSON.stringify(this.project),
        }
      );
    },
  },
};
</script>
