<template>
  <section class="util__container">
    <component
      v-if="story.content.component"
      :key="story.content._uid"
      :blok="story.content"
      :is="story.content.component">
    </component>
  </section>
</template>

<script>
import storyblokLivePreview from '@/mixins/storyblockLivePreview'

export default {
  data() {
    return {
      story: {
        content: {}
      }
    }
  },
  mixins: [storyblokLivePreview],
  asyncData(context) {
    let version = context.query._storyblok || context.isDev ? 'draft' : 'published'

    return context.app.$storyapi.get('cdn/stories/home', {
      version: version
    }).then((res) => {
      return res.data
    }).catch((res) => {
      context.error({ statusCode: res.response.status, message: res.response.data })
    })
  },
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
