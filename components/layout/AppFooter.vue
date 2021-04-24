<template>
  <footer class="sticky-footer bg-white">
    <div class="container my-auto">
      <div class="copyright text-center my-auto">
        <span>Copyright &copy; {{ brand }}</span>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      brand: "Project Management 2021",
    };
  },
};
</script>