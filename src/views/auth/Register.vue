<template>
  <section class="marged">
    <h1>Créer un compte</h1>
    <form action="" v-on:submit.prevent="checkForm">
      <input-type v-model="email" type="email" name="Email" id="email" :error='emailError'></input-type>
      <input-type v-model="password" type="password" name="Mot de passe" id="password" restriction="Minimum 8 caractères" :error='passwordError'></input-type>
      <input-type v-model="confirmPassword" type="password" name="Confirmer le mot de passe" id="confirm_password" restriction="Minimum 8 caractères" :error='confirmPasswordError'></input-type>
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
      confirmPassword: '',
      emailError: '',
      passwordError: '',
      confirmPasswordError: ''
    }
  },
  methods: {
    checkForm: function () {
      if (this.email.length === 0) {
        this.emailError = 'Veuillez renseigner un email'
      } else {
        const re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
        if (!re.test(String(this.email).toLowerCase())) {
          this.emailError = 'Email invalide'
        } else {
          this.emailError = ''
        }
      }
      this.passwordError = this.password.length < 8 ? '8 caractères minimum' : ''
      this.confirmPasswordError = this.confirmPassword.length < 8 ? '8 caractères minimum' : ''
      this.confirmPasswordError = this.confirmPassword !== this.password ? 'Les mots de passe doivent être identiques' : ''
      this.passwordError = this.password !== this.confirmPassword ? 'Les mots de passe doivent être identiques' : ''

      if (this.emailError === '' && this.passwordError === '' && this.confirmPasswordError === '') {
        console.log('Form OK')
      } else {
        console.log('Form not OK')
      }
    },
    changeUsername (username) {
      this.user.username = username
    }
  }
}
</script>
