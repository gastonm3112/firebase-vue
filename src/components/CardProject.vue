<template>
  <div class="card horizontal">
    <div class="card-stacked">
      <div class="card-content">
        <span class="card-title"> {{ data.name }} </span>
        <p>
          {{ data.description }}
        </p>
        <p>tecnologías: {{ data.langs }}</p>
      </div>
      <div class="card-action">
        <div class="row">
          <a class="col s6 waves-effect waves-light btn">
            <i class="material-icons">edit</i>
          </a>
          <a class="col s6 waves-effect waves-light btn red darken-1">
            <i class="material-icons">delete</i>
          </a>
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
};
</script>
