<template>
	<div class="container">
		<h2>Registrarme</h2>
 		<b-form @submit="onSubmit">
      <b-form-group id="exampleInputGroup1"
                    label="Email address:"
                    label-for="exampleInput1"
                    description="We'll never share your email with anyone else.">
        <b-form-input id="exampleInput1"
                      type="email"
                      v-model="form.email"
                      required
                      placeholder="Enter email">
        </b-form-input>
      </b-form-group>
      <b-form-group id="exampleInputGroup2"
                    label="Your Name:"
                    label-for="exampleInput2">
        <b-form-input id="exampleInput2"
                      type="text"
                      v-model="form.name"
                      required
                      placeholder="Enter name">
        </b-form-input>
      </b-form-group>
      <b-form-group id="exampleGroup4">
        <b-form-checkbox-group v-model="form.checked" id="exampleChecks">
          <b-form-checkbox value="me">Check me out</b-form-checkbox>
          <b-form-checkbox value="that">Check that out</b-form-checkbox>
        </b-form-checkbox-group>
      </b-form-group>

             <div v-cloak class="">
                <div v-show="serverError">
                  {{serverError}}
                </div>
              </div>
   </b-form>
		<form @submit.prevent="onSubmit">
          <vue-recaptcha
            ref="invisibleRecaptcha"
            @verify="onVerify"
            @expired="onExpired"
            size="invisible"
            :sitekey="sitekey">
          </vue-recaptcha>
          <button type="submit">Submit</button>
    </form>
					<div class="successful-server-response-wrapper" v-cloak>
            <div v-show="sucessfulServerResponse" class="successful-server-response">
              {{sucessfulServerResponse}}
            </div>
          </div>
	</div>
</template>
<script>
import VueRecaptcha from 'vue-recaptcha';

export default {
	auth: false,
	components: {
    'vue-recaptcha': VueRecaptcha
  },
	head () { return {
    script: [
      { src: 'https://www.google.com/recaptcha/api.js?onload=vueRecaptchaApiLoaded' }, 
    ]
	}},
	data () { return {
//		sitekey: '6LfofIMUAAAAAHgvZv7jdhz3M7TgN6EMHd-D0aii',
		sitekey: '6LfWfoMUAAAAAAEhjImNeGlg3x0juOEQnsxBOvfR',
		form: { email: "x@p.com"},
    sucessfulServerResponse: "",
    serverError: ""
	} },
  methods: {
    onSubmit: function () {
			console.log("onSubmit"); try {
      this.$refs.invisibleRecaptcha.execute()
			} catch (ex) { console.log("ERR",ex); }
    },
    onVerify: function (response) {
      console.log('Verify',response)
    },
    onExpired: function () {
      console.log('Expired')
    },
    resetRecaptcha () {
      this.$refs.recaptcha.reset() // Direct call reset method
    }
  }
}
</script>
