<template>
  <div class="wrapper">
    <div class="container my-5">
      <div class="row">
        <div class="col">
          <div v-if="$apollo.loading">Loading...</div>

          <div v-else>
            <h1 class="mb-3">{{ page.title }}</h1>
            <HtmlRender :html="page.content" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import pageQuery from '~/queries/single-page'

export default {
  data() {
    return {
      slug: 'about',
    }
  },
  apollo: {
    pageBy: {
      query: pageQuery,
      variables() {
        return {
          slug: this.slug,
        }
      },
    },
  },
  computed: {
    page() {
      return this.pageBy
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
