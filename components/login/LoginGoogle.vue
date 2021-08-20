<template>
  <a class="btn-icon" @click="loginGoogle()">
    <img
      width="16"
      height="16"
      src="https://d3ptyyxy2at9ui.cloudfront.net/google-41de20.svg"
    />
    Continue with Google
  </a>
</template>
<script>
export default {
  methods: {
    async loginGoogle() {
      await this.$auth.loginWith('google', {
        params: { prompt: 'select_account' },
      })
    },
  },
}
</script>