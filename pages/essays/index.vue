<template lang="pug">
.b-pt4.b-pb3
  main.Container(role="main")
    PostExcerptEssay(
      v-if="post.published && post.category === 'essay'"
      v-for="post in posts"
      :category="post.category"
      :date="post.date"
      :heroImage="post.heroImage"
      :heroImageNoShadow="post.heroImageNoShadow"
      :key="post.permalink"
      :lede="post.lede"
      :permalink="post.permalink"
      :readingTime="post.readingTime"
      :thumbImage="post.thumbImage"
      :tags="post.tags"
      :title="post.title"
    )
</template>

<script>
import PostExcerptEssay from "~/components/PostExcerptEssay.vue";

export default {
  name: "blog",
  components: {
    PostExcerptEssay
  },
  data() {
    return {
      posts: []
    };
  },
  async asyncData({ app }) {
    const posts = await app.$content("/posts").getAll();

    return {
      posts
    };
  },
  head() {
    return {
      title: "Essays—Callum Flack Design",
      meta: [
        {
          hid: "description",
          name: "description",
          content:
            "Essays by Callum Flack about design, user experience, code and the 'things inbetween' that inform their success"
        }
      ]
    };
  }
};
</script>
