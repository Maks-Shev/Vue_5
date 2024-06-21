<template>
  <form v-if="!isAuthenticated" action="#">
    <label for="login">Login</label>
    <input id="login" type="text" v-model="userLogin">
    <label for="password">Password</label>
    <input id="password" type="password" v-model="userPass">
    <button @click="formCheck" type="submit">Submit</button>
  </form>
  <h1 v-else>Авторизация успешна!</h1>
</template>

<script>
export default {
  name: 'AuthenticationComp',

  data () {
    return {
      isAuthenticated: false,
      userLogin: '',
      userPass: ''
    }
  },

  methods: {
    formCheck () {
      if (this.userLogin && this.userPass) {
        this.isAuthenticated = true
      } else {
        alert('Введите логин и пароль')
      }
    }
  }
}
</script>

<style lang="scss" scoped>

</style>

<!--Создайте компонент "Аутентификация" (Authentication), который
будет отображать форму входа или сообщение об успешной
аутентификации в зависимости от переданного пропса
isAuthenticated. Используйте директиву v-if для условного
отображения разных элементов в шаблоне компонента. -->
