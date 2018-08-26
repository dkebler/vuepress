<template>
  <div class="api">
      <object
        class="embed"
        :data="url"
        >
      </object>
  </div>
</template>

<script>
export default {
  computed: {
    data () {
      return this.$page.frontmatter
    },
    url () {
      const url =
        this.data.url ||
        this.data.staticDir +
          (this.data.defaultPage ? '/' + this.data.defaultPage + '.html' : '')
      console.log('url', url)
      return url
    }
  },
  methods: {
    toggleBodyClass (addRemoveClass, className) {
      const el = document.body

      if (addRemoveClass === 'add') {
        el.classList.add(className)
      } else {
        el.classList.remove(className)
      }
    }
  },
  mounted () {
    this.toggleBodyClass('add', 'no-scroll')
  },
  destroyed () {
    this.toggleBodyClass('remove', 'no-scroll')
  }
}
</script>

<style lang="stylus">
@import './styles/config.styl'

.no-scroll
  overflow-y hidden

.api
  padding $navbarHeight 0
  margin 0
  display flex
  .embed
    border-top 1px solid $borderColor
    padding 0
    margin-top 0
    flex-grow 1
    align-items flex-start
    align-content stretch
    height 100vh

@media (max-width: $MQMobile)
  .api
    .embed
      flex-direction column
    .feature
      max-width 100%
      padding 0

@media (max-width: $MQMobileNarrow)
  .api
    padding-left 0
    padding-right 0
</style>
