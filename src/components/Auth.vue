<template>
  <div class="container">
    <h1 class="center">{{ register ? 'Cadastro' : 'Login' }}</h1>
    <div class="auth-container">
      <ValidationObserver
        v-slot="{ invalid }"
      >
        <form @submit.prevent="submitHandler">

          <validation-provider
            v-if="register"
            rules="required|max:20"
            v-slot="{ errors }"
          >
            <input
              :class="errors[0] && 'invalid'"
              class="col"
              v-model="username"
              autofocus
              type="text"
              id="username"
              name="username"
              placeholder="Nome de usuário"
            >
            <div class="error">
              {{ errors[0] }}
            </div>
          </validation-provider>

          <validation-provider
            rules="required"
            v-slot="{ errors }"
          >
            <input
              :class="errors[0] && 'invalid'"
              class="col"
              v-model="email"
              :autofocus="!register"
              type="text"
              id="email"
              name="email"
              placeholder="Email"
            >
            <div class="error">
              {{ errors[0] }}
            </div>
          </validation-provider>

          <validation-provider
            rules="required|password"
            v-slot="{ errors }"
          >
            <input
              :class="errors[0] && 'invalid'"
              class="col"
              v-model="password"
              id="password"
              type="password"
              name="password"
              placeholder="Senha"
            >
            <div class="error">
              {{ errors[0] }}
            </div>
          </validation-provider>
          <div class="right">
            <button
              :disabled="invalid"
              class="btn-primary"
              type="submit"
            >
              Enviar
            </button>
          </div>
        </form>
      </ValidationObserver>
    </div>
  </div>
</template>

<script>
  import { ValidationObserver, ValidationProvider } from 'vee-validate'

  export default {
    components: {
      ValidationObserver,
      ValidationProvider
    },
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
        if (this.register) {
          this.$emit('registerSubmit', {
            username: this.username,
            email: this.email,
            password: this.password,
          })
        } else {
          this.$emit('loginSubmit', {
            email: this.email,
            password: this.password,
          })
        }
      }
    }
  }
</script>

<style scoped>
  .auth-container {
    max-width: 600px;
    margin-left: inherit;
    margin-right: inherit;
  }
  input {
    box-sizing: border-box;
    widows: 100%;
    height: 3em;
    margin: .5em 0 0;
    font-size: 1em;
  }
  .error {
    color: red;
  }
  input.invalid {
    border: 1px solid red;
  }
  button {
    height: 3em;
    font-size: 1em;
    margin: .5em 0 0;
  }
  button:disabled {
    border-color: gray;
    background-color: lightgray;
    color: darkgray;
  }
</style>
