<template>
  <div class="card">
    <picture>
      <!-- <source :srcset="featuredImage" /> -->
      <img :src="thumbnail" class="card-img-top" alt="Card image cap" />
    </picture>
    <div class="card-body">
      <h5 class="card-title">{{ post.title }}</h5>
      <HtmlRender :html="post.excerpt" class="card-text" />
      <NuxtLink :to="'/posts/' + post.slug" class="btn btn-primary">
        <h3>More</h3>
      </NuxtLink>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      default: null,
      type: Object,
    },
  },
  computed: {
    featuredImage() {
      return this.post && this.post.featuredImage
        ? this.post.featuredImage.node
        : ''
    },
    sizes() {
      return this.featuredImage && this.featuredImage.mediaDetails
        ? this.featuredImage.mediaDetails.sizes
        : ''
    },
    thumbnail() {
      const sizesArray = Array.from(JSON.parse(JSON.stringify(this.sizes)))
      const thumb = sizesArray.filter((item) => {
        return item.name === 'thumbnail'
      })

      return thumb[0] ? thumb[0].sourceUrl : ''
    },
  },
}
</script>

<style></style>
