<template lang="pug">
.b-pb3
  //- nav.Container.b-nav
    h3.Nav-locator.Meta.fw-700
      span.m-r2 1.
      span Blog
    //- .Extract-large
      hr
  Post(
    :body="page.body"
    :category="page.category"
    :date="page.date"
    :heroImage="page.heroImage"
    :heroImageNoShadow="page.heroImageNoShadow"
    :heroRatio="page.heroRatio"
    :link="page.permalink"
    :mostRecentPost = "page.mostRecentPost"
    :readingTime="page.readingTime"
    :tags="page.tags"
    :title="page.title"
    :updated="page.updated"
  )
  //- .Container.p-b7
    .figure.figure--post
      NewsletterSignupBlock
</template>

<script>
import Post from "~/components/Post.vue";

export default {
  components: {
    Post
  },
  data() {
    return {
      page: {}
    };
  },
  async asyncData({ app, route }) {
    const page = await app.$content("/posts").get(route.path);

    return {
      page
    };
  },
  head() {
    return {
      title: `${this.page.title}—Callum Flack Design`,
      meta: [
        {
          hid: "description",
          name: "description",
          content: `${this.page.title}—${this.page.lede}`
        }
      ]
    };
  }
};
</script>