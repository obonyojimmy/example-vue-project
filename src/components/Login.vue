<template>
  <div class="login col-sm-4 col-sm-offset-4">

    <page-title titleIcon="fa-lock" title="Login"></page-title>

    <p>Use the username: <strong>demouser</strong> password: <strong>testpass</strong></p>
    <div class="alert alert-danger" v-if="error">
      <p>{{ error }}</p>
    </div>
    <div class="form-group">
      <input 
        type="text"
        data-id="login.username" 
        class="form-control js-login__username"
        placeholder="Enter your username"
        v-model="credentials.username"
      >
    </div>
    <div class="form-group">
      <input
        type="password"
        class="form-control js-login__password "
        placeholder="Enter your password"
        v-model="credentials.password"
      >
    </div>
    <button 
      data-id="login.submit"
      class="btn btn-primary solid blank js-login__submit" 
      @click="submit()"
    >
      Login &nbsp; <i class="fa fa-arrow-circle-o-right"></i>
    </button>
    <br><br><br>
    <a href="#">Forgot your password?</a><br>
    Don’t have an account? &nbsp;<a href="#">Sign up here.</a>

  </div>
</template>

<script>
import Auth from '../auth'
import PageTitle from './PageTitle.vue'

export default {
  name: 'login',
  components: { PageTitle },
  beforeCreate () {
    this.auth = new Auth({ 'vue': this })
  },
  data () {
    return {
      credentials: {
        username: '',
        password: ''
      },
      error: ''
    }
  },
  methods: {
    submit () {
      var credentials = {
        username: this.credentials.username,
        password: this.credentials.password
      }
      this.auth.login(credentials, '/')
    }
  }
}
</script>

<style lang="scss" scoped>


</style>
