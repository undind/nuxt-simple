<template>
  <div>
    <top-header />
    <main role="main" id="main">
      <nuxt />
    </main>
    <bottom-footer />
  </div>
</template>

<script>
import TopHeader from '~/components/TopHeader.vue'
import BottomFooter from '~/components/BottomFooter.vue'

export default {
  components: {
    TopHeader,
    BottomFooter
  }
}
</script>

<style lang="scss">
@import '../assets/scss/style.scss';
</style>
