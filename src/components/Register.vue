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
    async validateUser() {
      if (
        this.pass1.length >= 6 &&
        this.pass1 === this.pass2 &&
        this.email != ""
      ) {
        const API_KEY = "AIzaSyBx0E4xI7MV8n5QBkVbzAllaaX6damASas";

        const res = await fetch(
          `https://identitytoolkit.googleapis.com/v1/accounts:signUp?key=${API_KEY}`,
          {
            method: "POST",
            body: JSON.stringify({
              email: this.email,
              password: this.pass1,
              returnSecureToken: true,
            }),
          }
        );

        console.log(await res.json());
      } else {
        return;
      }
    },
  },
};
</script>
