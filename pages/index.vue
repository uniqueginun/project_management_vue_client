<template>
  <div class="row">
    <div class="col-lg-6 d-none d-lg-block bg-login-image"></div>
    <div class="col-lg-6">
      <div class="p-5">
        <div class="text-center">
          <h1 class="h4 text-gray-900 mb-4">Project Manager</h1>
        </div>
        <form class="user" @submit.prevent="login">
          <div class="form-group">
            <input
              type="email"
              class="form-control form-control-user"
              id="exampleInputEmail"
              aria-describedby="emailHelp"
              placeholder="Enter Email Address..."
              v-model="form.email"
            />
          </div>
          <div class="form-group">
            <input
              type="password"
              class="form-control form-control-user"
              id="exampleInputPassword"
              placeholder="Password"
              v-model="form.password"
            />
          </div>
          <div class="form-group">
            <div class="custom-control custom-checkbox small">
              <input
                type="checkbox"
                class="custom-control-input"
                id="customCheck"
                v-model="form.remember_me"
              />
              <label class="custom-control-label" for="customCheck"
                >Remember Me</label
              >
            </div>
          </div>
          <button type="submit" class="btn btn-primary btn-user btn-block">
            Login
          </button>
        </form>
        <hr />
        <div class="text-center">
          <a class="small" href="forgot-password.html">Forgot Password?</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  layout: "guest",
  head: {
    titleTemplate: "%s - Login",
  },
  methods: {
    login() {
      console.log(this.form);
    },
  },
  data() {
    return {
      form: {
        email: "",
        password: "",
        remember_me: true,
      },
    };
  },
};
</script>