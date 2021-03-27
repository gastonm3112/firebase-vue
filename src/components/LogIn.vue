<template>
  <div class="container">
    <h2>Ingreso</h2>
    <p class="grey-text text-darken-1">
      Ingresa y comienza a ordenar tus tareas o proyectos
    </p>
    <div v-if="errors" class="card-panel red darken-2 white-text">
      <h5>Email / Password inválidos</h5>
    </div>
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
              v-model.trim="pass"
              id="password"
              type="password"
              class="validate"
            />
            <label for="password">Password</label>
          </div>
        </div>
        <button
          class="btn waves-effect waves-light"
          type="submit"
          name="action"
        >
          Sign In
        </button>
      </form>
    </div>
  </div>
</template>

<script>
import router from "../router/index";

export default {
  data: () => ({
    email: "",
    pass: "",
    errors: false,
  }),

  methods: {
    async validateUser() {
      if (this.pass.length >= 6 && this.email != "") {
        const API_KEY = "AIzaSyBx0E4xI7MV8n5QBkVbzAllaaX6damASas";

        const res = await fetch(
          `https://identitytoolkit.googleapis.com/v1/accounts:signInWithPassword?key=${API_KEY}`,
          {
            method: "POST",
            body: JSON.stringify({
              email: this.email,
              password: this.pass,
              returnSecureToken: true,
            }),
          }
        );

        const data = await res.json();

        if (data.error) {
          this.errors = true;
        } else {
          this.errors = false;
          console.log(data);
          localStorage.setItem("user", JSON.stringify(data));
          router.push("/proyectos");
        }
      } else {
        return;
      }
    },
  },
};
</script>
