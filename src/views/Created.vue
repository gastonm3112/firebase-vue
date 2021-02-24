<template>
  <div class="container">
    <div class="row">
      <form class="col s12">
        <div class="row">
          <div class="input-field col s12">
            <input id="project_name" type="text" class="validate" />
            <label for="project_name">Nombre del Proyecto</label>
          </div>
          <div class="input-field col s12">
            <input id="project_description" type="text" class="validate" />
            <label for="project_description">Descripción del Proyecto</label>
          </div>
          <p>
            <label>
              <input type="checkbox" />
              <span>HTML</span>
            </label>
          </p>
          <p>
            <label>
              <input type="checkbox" />
              <span>CSS</span>
            </label>
          </p>
          <p>
            <label>
              <input type="checkbox" />
              <span>JavaScript</span>
            </label>
          </p>
          <p>
            <label>
              <input type="checkbox" />
              <span>Vue</span>
            </label>
          </p>
          <p>
            <label>
              <input type="checkbox" />
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
};
</script>
