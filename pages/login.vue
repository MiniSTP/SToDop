<template>
<div class="login-body">
  <div class="login-box">
    <h2>Login</h2>
    <LoginGoogle/>
    <LoginFacebook/>
    <form method="post" @submit.prevent="login">
      <div class="user-box">
        <input v-model="email" type="text" name="" required="" />
        <label>Username</label>
      </div>
      <div class="user-box">
        <input v-model="password" type="password" name="" required="" />
        <label>Password</label>
      </div>
      <h4>
        <input type="checkbox" />
        Show password
      </h4>
      <Notification v-if="error" :message="error" />
      <a class="btn-submit" @click="login()">
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        Submit
      </a>
    </form>
    <h5>
      <a href="">Forget your password?</a>
    </h5>
    <h5>
      Don't have an account?
      <a href="/register">Sign up</a>
    </h5>
  </div>
</div>
</template>

<script>
import Notification from '~/components/Notification'
import LoginGoogle from '~/components/login/LoginGoogle'
import LoginFacebook from '~/components/login/LoginFacebook'

export default {
  name: 'Login',
  components: {
    Notification,
    LoginGoogle,
    LoginFacebook,
  },
  layout: 'clean',
  middleware: 'auth',
  auth: 'guest',

  data() {
    return {
      email: 'xy1z@gmail.com',
      password: '1',
      error: null,
    }
  },

  methods: {
    async login() {
      try {
        await this.$auth.loginWith('local', {
          data: {
            email: this.email,
            password: this.password,
          },
        })
        this.$router.push('/')
      } catch (e) {
        this.error = 'Username or Password not valid'
      }
    },
  },
}
</script>
<style src='@/assets/login.css'></style>
