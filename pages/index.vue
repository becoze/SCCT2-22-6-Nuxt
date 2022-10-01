
<template>
  <div class="body">
    <div class="logo">
      <img src="~/assets/logo-white.webp" alt="Dribl">
    </div>
    <div class="login-form">
      <div class="title-box">
        <h1> Sign In </h1>
      </div>
      <div class="message">
        <p> Welcome back! Please sign in. </p>
      </div>
      <div class="input-box">
        <input type="text" placeholder="Email address">  
        <input type="password" placeholder="Password">  
      </div> 
      <div class="forgot-pw">
        <a href="https://app.dribl.com/reset-password/"><button> Forgot password? </button></a>
      </div> 
      <div class="login-submit">
        <a @click="login()"> <button id="SignIn"> Sign in </button> </a> <br>
        <a href="http://localhost:3000/regi"><button id="Register"> Go to Register ... </button></a> <br>
        <p> Or </p>
        <a href="http://dribl-test.com/api/sociallogin/google"> <button id="SignIn-google"> <i class="fab fa-google"></i> Login with Google </button> </a>
        <a href="http://dribl-test.com/api/sociallogin/github"> <button id="SignIn-github"> <i class="fab fa-github"></i> Login with Github </button> </a>
        <a href="http://dribl-test.com/api/sociallogin/facebook"> <button id="SignIn-facebook"> <i class="fab fa-facebook"></i> Login with Facebook </button> </a>
        <p> By using Dribl, you agree to accept our <br> 
          <a href="https://www.dribl.com/privacy-policy.html"><button id="termsAndPolicy">Terms of Service</button></a>and
          <a href="https://www.dribl.com/privacy-policy.html"><button id="termsAndPolicy">Privacy Policy</button></a>
        </p>
      </div> 
    </div>
  </div> 
    
</template>




<script>
export default {
  methods: {
    login(){
      this.$auth.loginWith('laravelSanctum', {
        data: this.form
      })
      .then(response => console.log(response))
      .catch(error => console.log(error));
      // about axios and nuxt. https://laracasts.com/discuss/channels/vue/laravel-sanctum-nuxt-js-error-419-with-axios-post
    }
  },

  data(){
    return {
      form: {
        email: 'sample2@email.com',
        password: 'password'
      }
    }
  }

}
</script>

<style scoped> 
  input {
    outline: none;
  }
  .body{
    display: flex;
    background-color: #192536;
    width: 1920px;
    height: 980px;
  }
  .logo{
    display: flex;
    width: 960px;
    height: 980px;
    /* background-color: black; */
  }
  .logo img{
    width: 25%;
    display: block;
    margin: auto;
  }
  .login-form{
    width: 960px;
    height: 980px;
    background-color: #f0f3f4;
  }
  .title-box{
    height: 325px; /* 650/2=325 */
    line-height: 650px;
    margin: auto;
  }
  .title-box h1{
    text-align: center;
    color: #5b5b69;
  }
  
  .message{
    line-height: 30px;
    text-align: center;
    color: #6c757c;
  }
  .input-box{
    align-items: center;
    display: flex;
    flex-direction: column;
    margin-top: 20px;
    
  }
  input{
    width: 45%;
    height: 35px;
    margin-top: 20px;
    text-indent: 4px;  /* left space of placeholder */
    border: 1px solid #ced4da;
  }
  input:focus{
    border: 1px solid black;
  }
  .forgot-pw {
    text-align: center;
  }
  .forgot-pw button{
    border: none;
    color: #19a3b6;
    font-size: 12px;
    margin: 7px 0px 13px 330px;
  }
  .forgot-pw button:hover{
    cursor: pointer;
    color: #106773;
    text-decoration: underline;
  }
  .login-submit{
    text-align: center;
  }
  #SignIn{
    width: 440px;
    height: 40px;
    margin-left: auto;
    border: none;
    border-radius: 4px;
    background-color: #19a3b6;
    color: white;
  }
  #SignIn:hover{
    cursor: pointer;
    background-color: #148594;
  }

  #Register{
    width: 240px;
    height: 30px;
    margin-left: auto;
    margin-top: 10px;
  }

  #Register:hover{
    cursor: pointer;
  }

  #SignIn-google, #SignIn-github, #SignIn-facebook{
    width: 170px;
    height: 30px;
    margin-left: auto;
    border: none;
    border-radius: 5px;
    color: white;
  }
  #SignIn-google{
    background-color: #df4638;
  }

  #SignIn-github{
    background-color: #24292f;
  }
  #SignIn-facebook{
    background-color: #4f7ebc;
  }
  #SignIn-google:hover, #SignIn-github:hover, #SignIn-facebook:hover{
    border-style: outset;
  }
  #termsAndPolicy {
    border: none;
    color: #19a3b6;
  }
  
  #termsAndPolicy:hover {
    cursor: pointer;
    color: #106773;
    text-decoration: underline;
  }
</style>
