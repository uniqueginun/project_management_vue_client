<template>
  <!-- 404 Error Text -->
  <div class="text-center">
    <div class="error mx-auto">500</div>
    <p class="lead text-gray-800 mb-5">Opps, Something went wrong</p>
    <p class="text-gray-500 mb-0">
      It looks like you found a glitch in the matrix...
    </p>
    <nuxt-link to="/">&larr; Go Home</nuxt-link>
  </div>
</template>

<script>
export default {
  layout: "default",
};
</script>