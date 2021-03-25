<template>
  <div class="row">
    <div class="col s12 m7">
      <CardProject v-for="(project, i) in projects" :key="i" :data="project" />
    </div>
  </div>
</template>

<script>
import CardProject from "./CardProject.vue";
export default {
  data: () => ({
    projects: [],
  }),
  components: { CardProject },
  mounted() {
    this.getProjects();
  },
  methods: {
    //Llamado a la API de Firebase mediante metodo fetch.
    //.json debe colocarse al final de la URL
    async getProjects() {
      const user = JSON.parse(localStorage.getItem("user"));

      const res = await fetch(
        `https://crud-en-vue3-default-rtdb.firebaseio.com/projects.json?auth=${user.idToken}`
      );
      const data = await res.json();

      for (let i in data) {
        this.projects.push({
          id: i,
          data: data[i],
        });
        //console.log(data[i]);
      }

      //console.log(this.projects);
    },
  },
};
</script>
