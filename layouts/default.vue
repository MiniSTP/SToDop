<template>
  <div>
    <App v-if="isAuthenticated"/>
    <nuxt/>
  </div>
</template>

<script>
import { mapGetters } from 'vuex';
import App from '~/components/App';

export default {
  components: {
    App
  },
  computed:{
    ...mapGetters(['isAuthenticated'])
  }
}
</script>