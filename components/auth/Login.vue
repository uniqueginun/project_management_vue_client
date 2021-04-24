<template>
  <div class="row">
    <div class="col-lg-6 d-none d-lg-block bg-login-image"></div>
    <div class="col-lg-6">
      <div class="p-5">
        <div class="text-center">
          <h1 class="h4 text-gray-900 mb-4">Project Manager</h1>
        </div>
        <form @submit.prevent="login" class="user">
          <div class="form-group">
            <input
              type="text"
              class="form-control form-control-user"
              :class="{ 'is-invalid': errors.hasOwnProperty('personal_id') }"
              aria-describedby="emailHelp"
              placeholder="Enter Personal Id..."
              v-model="form.personal_id"
            />
            <div
              class="invalid-feedback"
              v-if="errors.hasOwnProperty('personal_id')"
            >
              {{ errors.personal_id[0] }}
            </div>
          </div>
          <div class="form-group">
            <input
              type="password"
              class="form-control form-control-user"
              :class="{ 'is-invalid': errors.hasOwnProperty('password') }"
              placeholder="Password"
              v-model="form.password"
            />
            <div
              class="invalid-feedback"
              v-if="errors.hasOwnProperty('password')"
            >
              {{ errors.password[0] }}
            </div>
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
          <button
            type="submit"
            :disabled="processing"
            class="btn btn-primary btn-user btn-block d-flex align-items-center justify-content-center"
          >
            <div class="font-weight-bolder">Login</div>
            <div v-if="processing" class="mx-3 spinner-border" role="status">
              <span class="sr-only">Loading...</span>
            </div>
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
  methods: {
    async login() {
      this.processing = true;
      try {
        await this.$auth.loginWith("laravelSanctum", {
          data: this.form,
        });
        const path = this.$auth.user.is_admin ? "admin/dashboard" : "dashboard";
        this.$router.replace({
          path,
        });
      } catch (error) {
        const { data, status } = error.response;
        if (status === 422) {
          this.errors = data.errors;
        }
        this.processing = false;
      }
    },
  },
  data() {
    return {
      processing: false,
      errors: {},
      form: {
        personal_id: "2420893055",
        password: "password",
        remember_me: true,
      },
    };
  },
};
</script>

<style scoped>
.invalid-feedback {
  margin-left: 10px;
}
</style>