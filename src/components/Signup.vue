<template>
    <form name="frm" action="localhost:8080/signup" method="post">
    <!-- Our application root element -->
    <div id="app">
      <b-container>
        <b-jumbotron header="Welcome to Pochat APP">
        </b-jumbotron>

        <b-form-group horizontal
                      :label-cols="3"
                      description="Let us know your name."
                      label="Your name"
        >
           <b-form-input v-model.trim="username" name="id"></b-form-input>
        </b-form-group>
        <b-form-group horizontal
                      :label-cols="3"
                      description="Let us know your password."
                      label="Password"
        >
           <input type="password" name="password" v-model.trim="password" class="form-control">
        </b-form-group>

        <b-alert variant="danger" :show="showAlert">{{ errMsg }}</b-alert>

		<b-btn variant="primary" @click="jssubmit">Login</b-btn>
        <b-btn variant="primary" v-on:click="href='/signup'">Signup</b-btn>
      </b-container>
    </div>
  	</form>
</template>

<script>
export default {
    data: function () {
        return {
            username: '',
            password: '',
            showAlert: false,
            errMsg: ''
        }
    },
    methods: {
        jssubmit: function() {
            if ( this.username == '' ) {
                this.showAlert = true;
                this.errMsg = 'Please enter your username';
                return;
            }
            if ( this.password == '' ) {
                this.showAlert = true;
                this.errMsg = 'Please enter the password';
                return;
            }
            this.showAlert = false;
            axios({
                method: 'post',
                url: "localhost:8080/login",
                data: {
                    username : this.username,
                    password : this.password
                }
            });
        }
    }
}
</script>
