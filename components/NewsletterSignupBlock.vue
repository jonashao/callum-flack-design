<template lang="pug">
  //- hr.Post-endRule.b-mb0.b-mt2
  //- .b-mt3--illusion
  .b-mt2
    //- .ff-title.fw-300(style="font-size:2em") ✺ 
    IconBase.BlackLittoralIcon(icon-name="icon-camp-fire" height="24" width="24")
      IconSun
    .rm-t2.fs-block-sm
      p Ps. I write a bi-monthly email letter about visual design, user experience and website development through the lens of people and attention. You should sign up:
      NewsletterSignupForm
</template>

<script>
import IconBase from "~/components/IconBase.vue";
import IconSun from "~/components/icons/IconSun.vue";
import NewsletterSignupForm from "~/components/NewsletterSignupForm.vue";

export default {
  components: {
    IconBase,
    IconSun,
    NewsletterSignupForm
  }
};
</script>

<style lang="postcss" scoped>
.b-mt3--illusion {
  margin-top: calc(2 * 0.7 * var(--responsive-space));
}

.BlackLittoralIcon {
  & >>> svg {
    border-radius: 999px;
    background-color: var(--c-text);
    color: var(--c-bg);
  }
}
</style>
