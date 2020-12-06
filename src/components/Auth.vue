<template>
  <div class="container">
    <h1>{{ register ? 'Cadastro' : 'Login' }}</h1>
    <div class="auth-container">
      <form @submit.prevent="submitHandler">
        <input
          v-if="register"
          v-model="username"
          autofocus
          type="text"
          id="username"
          name="username"
          placeholder="Nome de usuário"
        >
        <input
          v-model="email"
          :autofocus="!register"
          type="text"
          id="email"
          name="email"
          placeholder="Email"
        >
        <input
          v-model="password"
          id="password"
          type="password"
          name="password"
          placeholder="Senha"
        >
        <button

          type="submit"
        >
          Enviar
        </button>
      </form>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      register: {
        type: Boolean,
        required: true,
      },
    },
    data() {
      return {
        username: '',
        email: '',
        password: '',
      }
    },
    methods: {
      submitHandler() {
        console.log({
          username: this.username,
          email: this.email,
          password: this.password,
        })
      }
    }
  }
</script>

<style>

</style>
