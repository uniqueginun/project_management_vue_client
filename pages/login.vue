<template>
  <div>
    <login />
  </div>
</template>

<script>
import Login from "~/components/auth/Login.vue";
export default {
  components: { Login },
  layout: "guest",
  head: {
    titleTemplate: "%s - Login",
  },
};
</script>