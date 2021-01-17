<template>
  <section class="marged">
    <h1>Créer un compte</h1>
    <form action="" v-on:submit.prevent="checkForm">
      <input-type v-model="email" type="email" name="Email" id="email" :error='emailError'></input-type>
      <input-type v-model="password" type="password" name="Mot de passe" id="password" restriction="Minimum 8 caractères" :error='passwordError'></input-type>
      <input-type v-model="confirmPassword" type="password" name="Confirmer le mot de passe" id="confirm_password" restriction="Minimum 8 caractères" :error='confirmPasswordError'></input-type>
      <p class="errors" v-for="apiError in apiErrors" :key="apiError">
        {{ apiError[0] }}
      </p>
      <button>Créer un compte</button>
    </form>
  </section>
</template>

<script>
import InputType from '../../components/form/InputType'
import axios from 'axios'
import md5 from 'js-md5'

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
      confirmPasswordError: '',
      apiErrors: []
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
        axios
          .get('http://127.0.0.1:8000/api/register', {
            headers: {
              token: '1234'
            },
            params: {
              email: this.email,
              password: md5(this.password.toUpperCase())
            }
          })
          .then(response => {
            if (response.data.errors) {
              const errors = JSON.parse(JSON.stringify(response.data.errors))
              this.emailError = errors.email ? errors.email[0] : ''
              this.passwordError = errors.password ? errors.password[0] : ''
            }
            if (response.data.accepted) {
              console.log(response.data.token)
              localStorage.token = response.data.token
              // Stocking auth status as a cookie ? or just storage ?
              // Then redirect to home page
              // On redirige vers une page connecté mais avant on stock
            }
            console.log(response)
          })
      }
    },
    changeUsername (username) {
      this.user.username = username
    }
  }
}
</script>
