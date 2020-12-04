<template>
  <div class="container my-3">
    <div class="row">
      <div class="col">
        <b-nav pills>
          <b-nav-item to="/">Home</b-nav-item>
          <b-nav-item to="/about">About</b-nav-item>
        </b-nav>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    isActive(path) {
      return path === this.$route.path ? 'active' : ''
    },
  },
}
</script>

<style></style>
