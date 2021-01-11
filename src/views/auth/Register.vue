<template>
  <section class="marged">
    <h1>Créer un compte</h1>
    <form action="" v-on:submit.prevent="checkForm">
      <input-type v-model="email" type="email" name="Email" id="email"></input-type>
      <input-type v-model="password" type="password" name="Mot de passe" id="password" restriction="Minimum 8 caractères"></input-type>
      <input-type v-model="confirmPassword" type="password" name="Confirmer le mot de passe" id="confirm_password" restriction="Minimum 8 caractères"></input-type>
      <button>Créer un compte</button>
    </form>
  </section>
</template>

<script>
import InputType from '../../components/form/InputType'

export default {
  name: 'Register',
  components: {
    InputType
  },
  data: function () {
    return {
      email: '',
      password: '',
      confirmPassword: ''
    }
  },
  methods: {
    displayPassword: function (id) {
      if (id === 'password') {
        this.hidePassword = this.hidePassword === 'password' ? 'text' : 'password'
      } else if (id === 'password_confirm') {
        this.hideConfirmPassword = this.hideConfirmPassword === 'password' ? 'text' : 'password'
      }
    },
    checkForm: function () {
      console.log(this.email)
      console.log(this.password)
      console.log(this.confirmPassword)
    },
    changeUsername (username) {
      this.user.username = username
    }
  }
}
</script>
