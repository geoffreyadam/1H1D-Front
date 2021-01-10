<template>
  <section class="marged">
    <h1>Créer un compte</h1>
    <common-star></common-star>
    <form action="" v-on:submit.prevent="checkForm">
      <section>
        <label for="email">Email</label>
        <input v-model="email" type="email" id="email">
        <p v-if="errors.include('email')"></p>
      </section>
      <section>
        <label for="password">
          <span>Mot de passe</span>
          <div v-on:click="displayPassword('password')">
            <svg v-show="hidePassword === 'password'" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-eye-fill" viewBox="0 0 16 16">
              <path d="M10.5 8a2.5 2.5 0 1 1-5 0 2.5 2.5 0 0 1 5 0z"/>
              <path d="M0 8s3-5.5 8-5.5S16 8 16 8s-3 5.5-8 5.5S0 8 0 8zm8 3.5a3.5 3.5 0 1 0 0-7 3.5 3.5 0 0 0 0 7z"/>
            </svg>
            <svg v-show="hidePassword === 'text'" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-eye-slash-fill" viewBox="0 0 16 16">
              <path d="M10.79 12.912l-1.614-1.615a3.5 3.5 0 0 1-4.474-4.474l-2.06-2.06C.938 6.278 0 8 0 8s3 5.5 8 5.5a7.027 7.027 0 0 0 2.79-.588zM5.21 3.088A7.028 7.028 0 0 1 8 2.5c5 0 8 5.5 8 5.5s-.939 1.721-2.641 3.238l-2.062-2.062a3.5 3.5 0 0 0-4.474-4.474L5.21 3.088z"/>
              <path d="M5.525 7.646a2.5 2.5 0 0 0 2.829 2.829l-2.83-2.829zm4.95.708l-2.829-2.83a2.5 2.5 0 0 1 2.829 2.829zm3.171 6l-12-12 .708-.708 12 12-.708.707z"/>
            </svg>
          </div>
        </label>
        <small>Minimum 8 caractères</small>
        <input v-model="password" :type="hidePassword" id="password">
        <p v-if="errors.include('password')"></p>
      </section>
      <section>
        <label for="password_confirm">
          <span>Confirmation mot de passe</span>
          <div v-on:click="displayPassword('password_confirm')">
            <svg v-show="hideConfirmPassword === 'password'" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-eye-fill" viewBox="0 0 16 16">
              <path d="M10.5 8a2.5 2.5 0 1 1-5 0 2.5 2.5 0 0 1 5 0z"/>
              <path d="M0 8s3-5.5 8-5.5S16 8 16 8s-3 5.5-8 5.5S0 8 0 8zm8 3.5a3.5 3.5 0 1 0 0-7 3.5 3.5 0 0 0 0 7z"/>
            </svg>
            <svg v-show="hideConfirmPassword === 'text'" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-eye-slash-fill" viewBox="0 0 16 16">
              <path d="M10.79 12.912l-1.614-1.615a3.5 3.5 0 0 1-4.474-4.474l-2.06-2.06C.938 6.278 0 8 0 8s3 5.5 8 5.5a7.027 7.027 0 0 0 2.79-.588zM5.21 3.088A7.028 7.028 0 0 1 8 2.5c5 0 8 5.5 8 5.5s-.939 1.721-2.641 3.238l-2.062-2.062a3.5 3.5 0 0 0-4.474-4.474L5.21 3.088z"/>
              <path d="M5.525 7.646a2.5 2.5 0 0 0 2.829 2.829l-2.83-2.829zm4.95.708l-2.829-2.83a2.5 2.5 0 0 1 2.829 2.829zm3.171 6l-12-12 .708-.708 12 12-.708.707z"/>
            </svg>
          </div>
        </label>
        <small>Minimum 8 caractères</small>
        <input v-model="confirmPassword" :type="hideConfirmPassword" id="password_confirm">
        <p v-if="errors.include('passwordConfirm')"></p>
      </section>
      <button>Créer un compte</button>
    </form>
  </section>
</template>

<script>

import CommonStar from '../../components/Common-star'

export default {
  name: 'Register',
  components: {
    CommonStar
  },
  data: function () {
    return {
      hidePassword: 'password',
      hideConfirmPassword: 'password',
      email: '',
      password: '',
      confirmPassword: ''
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
