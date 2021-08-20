<template>
  <section class="section">
    <div class="container">
      <h1 class="title">STodoP</h1>
      <a href="/login">Login</a>
      <br>
      <a @click="logout()">Logout</a>
    </div>
  </section>
</template>

<script>
export default {
  middleware: 'auth',
  async beforeMount(){
    // console.log('auth executed')
    if (!this.$auth.loggedIn) {
      return
    }
  
    if(this.$auth.strategy.name === 'google'){  
      try {
        const rp = await this.$axios.$post('/user/login/google', {
            email: this.$auth.user.email,
            userName: this.$auth.user.name,
            avata: this.$auth.user.picture,
        });
        this.$auth.setToken('local', "Bearer "+ rp.data.token)
        this.$auth.setStrategy('local')
        this.$auth.fetchUser()
      } catch (e) {
        // console.log(e);
      }
    }
    this.$router.push('/profile')
  },
  methods:{
  async logout(){
    await this.$auth.logout()
  }
}
}

</script>
