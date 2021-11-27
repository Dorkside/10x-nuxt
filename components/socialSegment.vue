<template>
  <div
    class="social-container"
  >
    <a
      href="https://github.com/Dorkside"
      target="_blank"
      @mouseover="hoverGithub = true"
      @mouseleave="hoverGithub = false"
    >
      <ph-github-logo
        color="white"
        size="14vw"
        class="social-logo"
        :weight="hoverGithub ? 'fill' : 'regular'"
      />
    </a>
    <a
      href="https://www.linkedin.com/in/dorkside/"
      target="_blank"
      @mouseover="hoverLinkedin = true"
      @mouseleave="hoverLinkedin = false"
    >
      <ph-linkedin-logo
        color="white"
        size="14vw"
        class="social-logo"
        :weight="hoverLinkedin ? 'fill' : 'regular'"
      />
    </a>
    <a
      href="https://medium.com/@dorkside"
      target="_blank"
      @mouseover="hoverMedium = true"
      @mouseleave="hoverMedium = false"
    >
      <ph-medium-logo
        color="white"
        size="14vw"
        class="social-logo"
        :weight="hoverMedium ? 'fill' : 'regular'"
      />
    </a>
  </div>
</template>
<script>
import { PhLinkedinLogo, PhGithubLogo, PhMediumLogo } from 'phosphor-vue'

export default {
  name: 'SocialSegment',
  components: {
    PhLinkedinLogo,
    PhGithubLogo,
    PhMediumLogo
  },
  data () {
    return {
      hoverLinkedin: false,
      hoverGithub: false,
      hoverMedium: false
    }
  }
}
</script>
<style lang="scss" scoped>
.social-container {
  display: flex;
  flex-flow: row nowrap;
}
</style>
