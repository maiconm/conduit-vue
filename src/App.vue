<template>
  <div id="app">
    <Header />
    <router-view
      @loginSubmit="loginSubmitHandler"
      @registerSubmit="registerSubmitHandler"
    />
  </div>
</template>

<script>
import Header from './components/Header'

export default {
  methods: {
    loginSubmitHandler(dados) {
      console.log('login',dados)
    },
    registerSubmitHandler(dados) {
      console.log('cadastro', dados)
    },
  },
  name: 'App',
  components: {
    Header
  }
}
</script>

<style>
</style>
