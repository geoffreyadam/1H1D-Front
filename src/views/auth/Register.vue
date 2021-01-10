<template>
  <section class="marged">
    <h1>Créer un compte</h1>
    <form action="" v-on:submit.prevent="checkForm">
      <input-type type="email" name="Email" id="email" restriction=""></input-type>
      <input-type type="password" name="Mot de passe" id="password" restriction="Minimum 8 caractères"></input-type>
      <input-type type="password" name="Confirmer le mot de passe" id="confirm_password" restriction="Minimum 8 caractères" error="aucune"></input-type>
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
      hidePassword: 'password',
      hideConfirmPassword: 'password',
      email: '',
      password: '',
      confirmPassword: '',
      errors: []
    }
  },
  methods: {
    displayPassword: function (id) {
      console.log(id)
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
    }
  }
}
</script>
