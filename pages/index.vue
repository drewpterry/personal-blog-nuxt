<template>
  <div id="home-page" class="page-wrapper home-page">
    <site-hero :title="title" :subtitle="subtitle" :image="featureImage">
      <figure class="image is-32x32 is-inline-block">
        <a href="https://www.linkedin.com/in/drewpterry/">
          <img src="~/assets/uploads/linkedin-icon.svg" />
        </a>
      </figure>
      <figure class="image is-32x32 is-inline-block">
        <a href="https://github.com/drewpterry">
          <img src="~/assets/uploads/github-icon.svg" />
        </a>
      </figure>
      <figure class="image is-32x32 is-inline-block">
        <a href="https://twitter.com/drewpterry">
          <img src="~/assets/uploads/twitter-icon.svg" />
        </a>
      </figure>
    </site-hero>
    <main-section theme="one-column">
      <template v-slot:default>
        <!-- All Posts -->
        <posts-grid />
      </template>
      <template v-slot:sidebar>
        Nothing here
      </template>
    </main-section>
    <news-letter-form-modal />
  </div>
</template>

<script>
import { mapState } from 'vuex'
import { setPageData } from '../helper'
import NewsLetterFormModal from '~/components/NewsLetterFormModal'

export default {
  name: 'HomePage',
  head() {
    return {
      title: `Home | ${this.$siteConfig.siteName}`
    }
  },
  components: {
    NewsLetterFormModal
  },
  computed: {
    ...mapState(['title', 'subtitle', 'featureImage'])
  },
  fetch({ store, params }) {
    setPageData(store, { slug: 'home' })
  }
}
</script>

<style>
.home-page .under-subtitle {
  border-top: none;
}
</style>
