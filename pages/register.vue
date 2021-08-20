<template>
  <div class="login-box">
    <h2>Sign up</h2>
    <LoginGoogle/>
    <LoginFacebook/>
    <form>
      <div class="user-box">
        <input v-model="email" type="text" name="" required="" />
        <label>Email</label>
      </div>
      <div class="user-box">
        <input v-model="username" type="text" name="" required="" />
        <label>Name</label>
      </div>
      <div class="user-box">
        <input v-model="password" type="password" name="" required="" />
        <label>Password</label>
      </div>
      <div class="user-box">
        <input v-model="confirmPassword" type="password" name="" required="" />
        <label>Confirm Password</label>
      </div>
      <Notification v-if="error.length" :message="error" />
      <a class="btn-submit" @click="register()">
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        Register
      </a>
    </form>
    <h5>
      Already signed up??
      <a href="/login">Sign in</a>
    </h5>
  </div>
</template>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/2.1.1/jquery.min.js"></script>
<script>
import Notification from '~/components/Notification'
import LoginGoogle from '~/components/login/LoginGoogle'
import LoginFacebook from '~/components/login/LoginFacebook'
export default {
  components: {
    Notification,
    LoginGoogle,
    LoginFacebook,
  },
  middleware: 'auth',
  auth: 'guest',
  data() {
    return {
      email:'',
      username:'',
      password:'',
      confirmPassword:'',
      error: '',
    }
  },
  methods: {
    isChecked() {
      this.error=''
      if (!this.password) this.error = "Password couldn't null"
      if (!this.username) this.error = "Name couldn't null"
      if (this.password !== this.confirmPassword.trim())
        this.error = 'Confirm Password Wrong!!!'

      const re = new RegExp("[a-z0-9._%+-]+@[a-z0-9.-]+.[a-z]{2,4}$")
      if (!re.test(this.email)) this.error = 'Email Format Wrong!!!'
      if (this.error) return false
      return true
    },
    async register() {
      if (this.isChecked())
        try {
          const response = await this.$axios.post('/user/register', {
            userName: this.username,
            email: this.email,
            password: this.password,
          })
          if (response.data.status == 200) {
            await this.$auth.loginWith('local', {
              data: {
                email: this.email,
                password: this.password,
              },
            })
            this.$router.push('/')
          } else {
            this.error = response.data.message
          }
        } catch (e) {
          this.error = 'Lỗi rồi Đại Vương ơi...'
        }
    },
  },
}
</script>
<style src='@/assets/login.css'></style>
