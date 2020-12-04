<script>
export default {
  props: {
    html: {
      default: '',
      type: String,
    },
  },
  // computed: {
  //   dynamicComponent() {
  //     return {
  //       template: `<div>${this.html}</div>`,
  //     }
  //   },
  // },
  render(createElement, context) {
    return createElement({
      template: `<div>${this.html}</div>`,
    })
  },
}
</script>

<style></style>
