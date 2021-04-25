<template>
  <div>
    <login />
  </div>
</template>

<script>
import Login from "~/components/auth/Login.vue";
export default {
  middleware: "auth",
  auth: "guest",
  components: { Login },
  layout: "guest",
  head: {
    titleTemplate: "%s - Login",
  },
};
</script>