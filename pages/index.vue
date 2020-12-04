<template>
  <div class="container">
    <h1>Blog list</h1>
    <div v-if="$apollo.loading">Loading...</div>
    <div v-else>
      <div class="container">
        <div class="row">
          <div v-for="post in postsList" :key="post.id" class="mb-5 col-md-4">
            <CardPost :post="post.node" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import posts from '~/queries/posts-query'

export default {
  apollo: {
    posts,
  },
  computed: {
    postsList() {
      return this.posts ? this.posts.edges : null
    },
  },
}
</script>

<style>
img {
  max-width: 100%;
  margin-bottom: 30px;
}
.gallery {
  list-style: none;
  padding: 0;
}
.gallery li {
  padding: 0;
}
</style>
