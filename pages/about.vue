<template lang="pug">
div
  //- nav.Container.b-nav
    h3.Nav-locator.Meta.fw-700
      span.m-r2 5.
      span About
  article.b-pt4.b-pb3
    //- header.CoverImage.rp-t2(role="banner")
    header.CoverImage(role="banner")
      .Container
        .Extract-super
          .AspectRatio.md-AspectRatio--10x4
            .AspectRatio-object.bg-text
              ImageCld(src="https://res.cloudinary.com/pw-img-cdn/image/upload/v1533123284/okok/cf-dwts-01-16x9.jpg")
            .AspectRatio-object.Blend
              .Container
                .Extract-large.h-100
                  .f.f-alignItemsCenter.h-100
                    //- .w-8x12.w-md-9x12.w-lg-8x12
                    div
                      h1.Title.fw-600.c-bg.m-b0
                        //- | Working at the intersection between user experience, visual design &amp; code.
                        //- | Visual design plus user experience plus code.
                        | Working within
                        br
                        | visual design,
                        br
                        | user experience
                        br 
                        | and code.
                      //- h2.Subheading.fw-400.c-bg.w-10x12
                        | “…if the solution is not beautiful, I know it is wrong.” 
                        span.fs-scale-reset #[span.Meta — Buckminster Fuller]
                      h2.Text.fw-400.c-bg.w-lg-8x12.u-hidden.u-sm-block.rm-t4
                        span.Text--italic The quality of the connections is the key to quality.
                        br 
                        span.Blockquote-author — Charles Eames
      
    main(role="main")
      .Container.b-pt3
        .Scope-post.Scope-post-dropcap
          nuxtent-body(:body="page.body")

</template>

<script>
import ImageCld from "~/components/ImageLazyCldOrig.vue";

/* src-placeholder="https://res.cloudinary.com/pw-img-cdn/image/fetch/w_50,e_blur:300/https://res.cloudinary.com/pw-img-cdn/image/upload/v1533123284/okok/cf-dwts-01-16x9.jpg" */

export default {
  components: {
    ImageCld
  },
  props: {
    title: String,
    lede: String,
    heroImage: String
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
  },
  scrollToTop: false,
  async asyncData({ app, route }) {
    return {
      page: await app.$content("/pages").get(route.path)
    };
  }
};
</script>

<style lang="postcss" scoped>
@import "../assets/styles/variables.css";

.Blend {
  background-blend-mode: multiply;
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.9) 40%, rgba(0, 0, 0, 0.05) 80%);
}

.w-su-5x12 {
  @media (--su) {
    width: calc(6 / 12 * 100%) !important;
  }
}
</style>
