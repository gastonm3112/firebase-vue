<template>
  <div class="container">
    <h2>Registrar Usuario</h2>
    <div class="row">
      <form @submit.prevent="validateUser" class="col s12">
        <div class="row">
          <div class="input-field col s12">
            <input
              v-model.trim="email"
              id="email"
              type="email"
              class="validate"
            />
            <label for="email">Email</label>
          </div>
        </div>
        <div class="row">
          <div class="input-field col s12">
            <input
              v-model.trim="pass1"
              id="password"
              type="password"
              class="validate"
            />
            <label for="password">Password</label>
          </div>
        </div>
        <div class="row">
          <div class="input-field col s12">
            <input
              v-model.trim="pass2"
              id="passwordConfirm"
              type="password"
              class="validate"
            />
            <label for="passwordConfirm">Confirmar Password</label>
          </div>
        </div>
        <button
          class="btn waves-effect waves-light"
          type="submit"
          name="action"
        >
          Submit
          <i class="material-icons right">send</i>
        </button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    email: "",
    pass1: "",
    pass2: "",
  }),

  methods: {
    validateUser() {
      if (
        this.pass1.length >= 6 &&
        this.pass1 === this.pass2 &&
        this.email != ""
      ) {
        return console.log("Contraseña valida");
      } else {
        return;
      }
    },
  },
};
</script>
