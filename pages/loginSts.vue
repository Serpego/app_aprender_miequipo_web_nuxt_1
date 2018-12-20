<template>
  <section class="container">
    <div>
      <h1 class="title">
        prueba
      </h1>
			<p>User: {{$auth.user}}</p>
			<p>Logedin: {{$auth.loggedIn}}</p>
			<p>TokenG: {{$auth.getToken('google')}}</p>
			<p>TokenF: {{$auth.getToken('facebook')}}</p>

			<b-btn @click="$auth.logout()">Logout</b-btn>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
	auth: false,
  components: {
    Logo
  },
	methods: {
		loginFb () { this.$auth.loginWith('facebook'); }
	},
}
</script>

<style>
</style>
