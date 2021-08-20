<template>
    <a class="btn-icon" @click="loginFacebook()">
      <img
        width="16"
        height="16"
        src="https://d3ptyyxy2at9ui.cloudfront.net/facebook-fadd25.svg"
      />
      Continue with Facebook
    </a>
</template>
<script>
export default {
  methods: {
    async loginFacebook(){
      await this.$auth.loginWith('facebook')
    },
  },
}
</script>