<template lang="pug">
  //- article.rp-t2(:style="postExcerptBlockColor")
  article(:style="postExcerptBlockColor")
    header.b-pb2(role="banner")
      .Container.b-pt4
        .b-pb2.w-lg-5x6.m-xA
          h1.Title.u-textCenter.rm-b2 {{ title }}
          .Meta.c-textLight.u-textCenter.p-t1(v-if="category !== 'projects'")
            //- time(:date-time="date") {{ date | moment("MMMM Do, YYYY") }}
            time(:date-time="date") {{ date | moment("YYYY.MM.DD") }}
            span.MetaSeparator • 
            span.u-textCapitalise {{ category }}
            span.MetaSeparator(v-if="readingTime" ) • 
            span(v-if="readingTime" ) {{ readingTime }} minutes
          .Meta.c-textLight.u-textCenter.p-t1(v-else)
            time(:date-time="date") {{ date | moment("YYYY") }}
            span.MetaSeparator • 
            span.u-textCapitalise {{ category }}
            //- span.MetaSeparator •
            //- span {{ tags }}
        .m-a0(v-if="heroImage", :class="heroExtractClasses")
          .AspectRatio(:style="heroAspectStyle")
            //- .AspectRatio-object(:class="{ 'bg-text': !heroImageNoShadow }")
            .AspectRatio-object(:class="heroObjectBgClasses")
              ImageCld(:src="heroImage")

    main(role="main", v-if="body")
      .Container
        .Scope-post(:class="scopeClasses")
          //- no-ssr
          nuxtent-body(:body="body")

        NewsletterSignupBlock

</template>

<script>
import moment from "vue-moment";
import ImageCld from "~/components/ImageLazyCldOrig.vue";
import NewsletterSignupBlock from "~/components/NewsletterSignupBlock.vue";

export default {
  name: "post",
  components: {
    moment,
    ImageCld,
    NewsletterSignupBlock
  },
  props: {
    body: Object,
    blockColor: String,
    category: {
      type: String,
      required: true
    },
    date: String,
    heroImage: String,
    heroImageNoShadow: {
      type: Boolean,
      default: false
    },
    heroRatio: {
      type: Number,
      default: 56.25
    },
    lede: String,
    link: String,
    mostRecentPost: {
      type: Boolean,
      default: false
    },
    note: String,
    permalink: String,
    published: Boolean,
    readingTime: Number,
    tags: {
      type: String,
      default: null
    },
    title: String,
    updated: Boolean
  },
  computed: {
    postExcerptBlockColor() {
      return this.blockColor && `background-color: ${this.blockColor}`;
    },
    postExcerptLede() {
      return this.$route.name === "blog-page" && this.mostRecentPost;
    },
    /* headerClasses() {
      if (this.$route.name === "blog-page") {
        return "b-pb2";
      }
    }, */
    heroExtractClasses() {
      if (this.category === "projects") {
        return "Extract-super";
      }
      return "Extract-hero";
    },
    heroAspectClasses() {
      return this.heroRatio && `AspectRatio--${this.heroRatio}`;
    },
    heroAspectStyle() {
      return this.heroRatio && `padding-bottom: ${this.heroRatio}%`;
    },
    heroObjectBgClasses() {
      // const shadow = !this.heroImageNoShadow && "bg-text";
      // const project = this.category === "projects" && "Project-hero";
      // return { shadow, project };
      // if (this.category === "projects" && !this.heroImageNoShadow) {
      //   return "Project-hero-shadow bg-text";
      // }
      // return "bg-text";
      return !this.heroImageNoShadow && "bg-text";
    },
    scopeClasses() {
      // return this.category === "essays" && "Scope-post-figure Scope-post-dropcap";
      return this.category === "essay" && "Scope-post-dropcap";
    }
  }
};
</script>
