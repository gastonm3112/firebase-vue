<template>
  <div class="card horizontal" v-if="data.data.status">
    <div class="card-stacked">
      <div class="card-content">
        <span class="card-title"> {{ data.data.title }} </span>
        <p>
          {{ data.data.description }}
        </p>
        <p>
          tecnologías:
          <span v-for="(lang, i) in data.data.langs" :key="i">
            {{
              i < data.data.langs.length - 1
                ? `${lang}, `.toUpperCase()
                : lang.toUpperCase()
            }}
          </span>
        </p>
      </div>
      <div class="card-action">
        <div class="row">
          <router-link
            :to="`/edit-projects/${data.id}`"
            class="col s6 waves-effect waves-light btn"
          >
            <i class="material-icons">edit</i>
          </router-link>
          <button
            @click="deleteProject"
            class="col s6 waves-effect waves-light btn red darken-1"
          >
            <i class="material-icons">delete</i>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    data: Object,
  },
  methods: {
    async deleteProject() {
      const id = this.data.id;

      const res = await fetch(
        `https://crud-en-vue3-default-rtdb.firebaseio.com/projects/${id}.json`,
        {
          method: "PATCH",
          body: JSON.stringify({ status: false }),
        }
      );

      const data = await res.json();

      //Elimina la vista de las Cards de forma reactiva
      this.data.data.status = data["status"];
    },
  },
};
</script>
