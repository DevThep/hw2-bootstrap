<template>
  <div class="container col-md-4 col-md-offset-4 sign-in">
    <h2>Login</h2>
  	<b-form-input v-model="email" type="text" placeholder="Enter your email"></b-form-input>
  	<br>
  	<b-form-input v-model="password" type="password" placeholder="Enter your password"></b-form-input>
  	<div class="sub-button">
  		<b-button size="md" variant="primary" @click="login">Login</b-button>
  	</div>
  </div>
  
</template>

<script>
import UsersApi from '../api/users.js'
import router from '../router'

export default {
  name: 'sign-in',
  data () {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    login () {
      console.log('methods.login')
      UsersApi.login(this.email, this.password, function (_response) {
        // NOTE: Posts.index is not yet implemented
        router.push({ name: 'Posts.index' })
      })
    }
  }
}
</script>

<style lang="css">
	.sign-in {
		padding-top: 70px;
	}

	.sub-button {
		text-align:center;
		padding-top: 20px;
	}

  h2 {
    padding-bottom: 10px;
    text-align: center;
  }
</style>
