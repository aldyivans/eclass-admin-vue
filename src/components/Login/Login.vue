<template>
  <div class="justify-content-center align-items-center w-100 d-flex" style="height: 100vh">
    <div class="col-12 col-sm-8 col-md-6 col-lg-4">
      <h5 class="text-center">Log In as an Admin</h5>
      <div class="text-center">
        <span class="text-danger" id="invalid"></span>
      </div>
      <form>
        <div class="form-group">
          <input type="text" class="form-control bg-light rounded-0" name="username" placeholder="Username" v-model="login.username" ref="loginUsername">
          <span class="text-danger" style="font-size: 12px" ref="inputWarning1"></span>
        </div>
        <div class="form-group">
          <input type="password" class="form-control bg-light rounded-0" name="password" placeholder="Password" v-model="login.password" ref="loginPassword">
          <span class="text-danger" style="font-size: 12px" ref="inputWarning2"></span>
        </div>
        <button type="button" style="font-weight: bold;" class="col-12 btn btn-primary rounded-0" v-on:click="save">Log In</button>
      </form>
    </div>
  </div>
</template>

<script>

import axios from 'axios'

export default {
  data() {
    return {
      login: {
        username: '',
        password: ''
      },
      url: 'http://192.168.2.231:3000/v1/login'
    }
  },
  methods: {
    save() {

      var loginUsername = this.$refs.loginUsername;
      var loginPassword = this.$refs.loginPassword;
      var inpWarning1 = this.$refs.inputWarning1;
      var inpWarning2 = this.$refs.inputWarning2;
      var invalid = this.$refs.invalid;
      var self = this;

      if(this.login.username == "") {
        loginUsername.style.borderBottom = "3px solid red"
        inpWarning1.innerHTML = "field cannot be empty!"
      } else {
        loginUsername.style.borderBottom = "1px solid #ccc"
            inpWarning1.innerHTML = ""
      }

      if(this.login.password == "") {
        loginPassword.style.borderBottom = "3px solid red"
        inpWarning2.innerHTML = "field cannot be empty!"
      } else {
        loginPassword.style.borderBottom = "1px solid #ccc"
            inpWarning2.innerHTML = ""
      }

      if(this.login.username != "" && this.login.password != "") {
        const headers = {
          'Authorization': localStorage.getItem('token'),
          'Content-Type':'application/json',
          'Accept': 'application/json',
          'Access-Control-Allow-Origin': '*',
          'Access-Control-Allow-Headers': 'X-Requested-With,Content-Type',
          // 'withCredentials': true,
        }

        var dataUser = {
          username: this.login.username.toLowerCase(),
          email: this.login.username.toLowerCase(),
          password: this.login.password
        }

        axios.post(this.url, dataUser, headers).then(response => {
          if(response.status === 200){
            localStorage.setItem('token', response.data.tokens)
            localStorage.setItem('ECLASS-id', response.data.ID)
            // console.log('Response', response)
            console.log(response)

            self.$root.$emit('isLoggedIn');
          }
        }).catch(e=>{
          console.log('error', e.response);
          invalid.innerHTML = "Invalid Username or Password!"
        })
      }
    }
  }
}

</script>