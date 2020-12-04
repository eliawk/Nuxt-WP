<template>
  <div class="container">
    <NuxtLink to="/" class="btn btn-primary">Home</NuxtLink>

    <div v-if="$apollo.loading">Loading...</div>

    <div v-else>
      <h1>{{ post.title }}</h1>

      <h5 v-if="post.post_details.subtitle">
        {{ post.post_details.subtitle }}
      </h5>
      <div class="details my-5">
        {{ post.post_details.year }}
        <ul class="gallery">
          <li v-for="item in post.post_details.block" :key="item.id">
            <img :src="item.image.mediaItemUrl" alt="" />
            <h5>{{ item.text }}</h5>
          </li>
        </ul>
      </div>

      <HtmlRender :html="post.content" />
    </div>
  </div>
</template>

<script>
import postQuery from '~/queries/single-post-query'

export default {
  computed: {
    slug() {
      return this.$route ? this.$route.params.slug : ''
    },
  },
  apollo: {
    post: {
      query: postQuery,
      variables() {
        return {
          slug: this.slug,
        }
      },
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
