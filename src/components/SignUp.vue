<template>
  <div class="signup">
    <h3>Sign Up</h3>
    <input type="text" placeholder="Email" v-model="email"><br>
    <input type="password" placeholder="Password" v-model="password"><br>
    <button @click="signUp">Sign Up</button>
    <p>Already have an account? <router-link to="/login">Login</router-link></p>
  </div>
</template>

<script>
import firebase from 'firebase'

export default {
  name: 'SignUp',
  data() {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    signUp() {
      firebase.auth().createUserWithEmailAndPassword(this.email, this.password).then(
          user => {
            this.$router.replace('home')
          },
          function(err) {
            alert('There was a problem creating your account' + err.message)
          }
        )
    }
  }
}
</script>

<style>
.signup {
  display: block;
  text-align: center;
}
</style>