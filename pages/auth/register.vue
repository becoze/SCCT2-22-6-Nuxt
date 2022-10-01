<template>
    <div class="body">
      <div class="logo">
        <img src="~/assets/logo-white.webp" alt="Dribl>" />
      </div>
      <div class="login-form">
        <div class="title-box"></div>
        <h1>Welcome to Dribl</h1>
        <h2>Sig in to your account</h2>
  
        <div>
          <div class="message"></div>
  
          <div class="input-box">
            <form @submit.prevent="login">
              <div class="form-group">
                <label>Email</label>
                <input
                  v-model="form.email"
                  type="email"
                  class="form-control"
                  :class="{ 'is-invalid': errors.email }"
                  placeholder="Email"
                />
                <div class="invalid-feedback" v-if="errors.email">
                  {{ errors.email[0] }}
                </div>
              </div>
              <div class="form-group">
                <label>Password</label>
                <input
                  v-model="form.password"
                  type="password"
                  class="form-control"
                  :class="{ 'is-invalid': errors.password }"
                  placeholder="Password"
                />
                <div class="invalid-feedback" v-if="errors.password">
                  {{ errors.password[0] }}
                </div>
              </div>
              <div class="form-group">
                <input
                  id="SignIn"
                  type="submit"
                  value="Login"
                  class="btn btn-light w-100"
                />
                <div class="forgot-pw">
                  <button>
                    <a href="https://app.dribl.com/reset-password/"
                      >Forgot password?</a
                    >
                  </button>
                </div>
                <div class="forgot-pw">
                  <button>
                    <a href="http://localhost:3000/auth/register">Or, Register</a>
                  </button>
                </div>
              </div>
            </form>
          </div>
  
          <div class="login-submit">
            <p>Or login with Social media accounts</p>
  
            <a href="https://dribl.app/api/login/google">
              <button
                @click="socialLogin('google')"
                class="social-login-btn google"
              >
                <i class="fab fa-google"></i>
              </button>
            </a>
            <a href="https://dribl.app/api/login/facebook">
              <button
                @click="socialLogin('github')"
                class="social-login-btn github"
              >
                <i class="fab fa-github"></i>
              </button>
            </a>
            <a href="https://dribl.app/api/login/github">
              <button
                @click="socialLogin('facebook')"
                class="social-login-btn facebook"
              >
                <i class="fab fa-facebook"></i></button
            ></a>
            <p>
              By using Dribl, you agree to accept our <br />
              <a class="External" href="https://www.dribl.com/privacy-policy.html"
                >Terms of Service</a
              >
              and
              <a href="https://www.dribl.com/privacy-policy.html"
                >Privacy Policy</a
              >
            </p>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  
  <script>
  // import SocialLogin from "@/components/SocialLogin";
  export default {
    middleware: "guest",
    components: {
      SocialLogin,
    },
    data() {
      return {
        form: {
          email: "",
          password: "",
        },
        error: this.$route.query.error,
      };
    },
    methods: {
      async login() {
        try {
          // await this.$auth.login({ data: this.form });
          await this.$axios.post("/auth/login", this.form);
        } catch (e) {
          return;
        }
        this.$router.push(
          this.$route.query.redirect ? this.$route.query.redirect : "/"
        );
      },
    },
  };
  </script>
  
  <style lang="scss" scoped>
  .social-login {
    display: flex;
    justify-content: center;
  }
  .social-login-btn {
    color: white;
    border-radius: 5px;
    background: #333;
    border: none;
    margin-bottom: 10px;
    margin-left: 5px;
    margin-right: 5px;
    width: 50px;
    height: 50px;
    font-size: 23px;
    cursor: pointer;
    &.google {
      background: #dd4b39;
    }
    &.github {
      background: #24292e;
    }
    &.facebook {
      background: #3b5998;
    }
  }
  input {
    outline: none;
  }
  .body {
    display: flex;
    background-color: #192536;
    width: 1300px;
    height: 980px;
    overflow: hidden;
  }
  .logo {
    display: flex;
    width: 770px;
    height: 590px;
    /* background-color: black; */
  }
  .logo img {
    width: 720%;
    display: block;
    margin: auto;
  }
  .login-form {
    width: 910px;
    height: 980px;
    background-color: #f0f3f4;
  }
  .title-box {
    height: 325px;
    /* 650/2=325 */
    line-height: 650px;
    margin: auto;
    text-align: center;
  }
  .title-box h1 {
    text-align: center;
    color: #5b5b69;
  }
  .message {
    line-height: 40px;
    text-align: center;
    color: #6c757c;
  }
  .input-box {
    align-items: center;
    display: flex;
    flex-direction: column;
    margin-top: 20px;
    width: 100%;
  }
  input:focus {
    border: 1px solid black;
  }
  .forgot-pw {
    text-align: center;
  }
  .forgot-pw button {
    border: none;
    color: #19a3b6;
    font-size: 12px;
    margin: 7px 0px 13px 330px;
  }
  .forgot-pw button:hover {
    cursor: pointer;
    color: #106773;
    text-decoration: underline;
  }
  .login-submit {
    text-align: center;
  }
  #SignIn {
    width: 840px;
    height: 40px;
    margin-left: auto;
    border: none;
    border-radius: 4px;
    background-color: #19a3b6;
    color: white;
  }
  #SignIn:hover {
    cursor: pointer;
    background-color: #148594;
  }
  #SignIn-google,
  #SignIn-github,
  #SignIn-facebook {
    width: 170px;
    height: 30px;
    margin-left: auto;
    border: none;
    border-radius: 5px;
    color: white;
  }
  #SignIn-google {
    background-color: #df4638;
  }
  #SignIn-github {
    background-color: #24292f;
  }
  #SignIn-facebook {
    background-color: #4f7ebc;
  }
  #SignIn-google:hover,
  #SignIn-github:hover,
  #SignIn-facebook:hover {
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
  h1,
  h2 {
    text-align: center;
  }
  </style>`