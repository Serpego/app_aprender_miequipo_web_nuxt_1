<template>
	<div>
	<b-jumbotron header="Podemos Aprender" lead="Armá tu equipo para trabajar, negocios y aprender." >
		<p>Para más información <b-link href="https://podemosaprender.org/contacto">contactanos</b-link></p>
		<div v-if="!$auth.loggedIn">
			<img id="bfb" @click="loginFb" size="sm" src="/btn_fb.png" alt="Continuar con Facebook">
			<img id="bgoog" @click="loginGoog" size="sm" src="/btn_google.png" alt="Continuar con Google">
			<b-btn to="registrarme" size="sm" variant="success">Registrarme</b-btn>
		</div>
	</b-jumbotron>

	</div>
</template>

<script>
export default {
	auth: false,
	methods: {
		loginFb () { var me= this; this.$auth.loginWith('facebook').then(() => console.log("TOK FB",me.$auth.user,me.$auth.getToken('facebook'))); },
		loginGoog () { var me= this; this.$auth.loginWith('google').then(() => console.log("TOK GG",me.$auth.user,me.$auth.getToken('google'))); }
	},
	created () {
		console.log("TOK GG",this.$auth.user,this.$auth.getToken('google'),this.$auth.getToken('facebook'));
	}
}
</script>

<style>
#bgoog { 
	cursor: pointer; 
	width: 11em;
	height: 2.19em;
}
#bfb { 
	cursor: pointer; 
	width: 11em;
	height: 2.1em;
}
</style>
