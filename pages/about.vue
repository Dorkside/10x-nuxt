<template>
  <main class="layout">
    <div class="logo-title">
      <div class="logo-container">
        <nuxt-img
          class="logo"
          src="/favicon.png"
        />
      </div>
    </div>
    <div class="segment-container">
      <div
        v-for="(segment,index) of contentSegments"
        :key="index"
        class="segment"
        :style="{flex: segment.width}"
      >
        <component
          :is="segment.type"
          :content="segment.content"
          :background-url="segment.backgroundUrl"
          :background-color="segment.backgroundColor"
          :background-attachment="segment.backgroundAttachment"
          :background-position="segment.backgroundPosition"
          :background-size="segment.backgroundSize"
          :background-repeat="segment.backgroundRepeat"
          :class="segment.class"
          :variant="segment.variant"
        />
      </div>
    </div>
  </main>
</template>
<script>
export default {
  name: 'About',
  data () {
    return {
      contentSegments: [{
        content: ['Hey!'],
        type: 'TextSegment',
        width: '100%'
      }, {
        content: ["I'm "],
        type: 'TextSegment'
      }, {
        content: ['James.'],
        type: 'KnockoutSegment'
      }, {
        content: ['Senior', 'Self-taught', 'Full-stack', 'Creative'],
        type: 'SlideSegment',
        width: '100%'
      }, {
        content: ['software developer.'],
        type: 'TextSegment'
      }, {
        content: ['I love'],
        type: 'TextSegment'
      }, {
        content: ['finding solutions.', 'creating stuff.', 'experimenting.', 'drinking beer.'],
        type: 'SlideSegment',
        width: '100%'
      }, {
        type: 'Spacer',
        width: '100%'
      }, {
        content: ['Half-Irish'],
        type: 'KnockoutSegment',
        backgroundUrl: 'images/irish.svg',
        backgroundAttachment: 'scroll'
      }, {
        content: ['Half-Breton'],
        type: 'KnockoutSegment',
        backgroundUrl: 'images/breton.svg',
        backgroundPosition: 'top center',
        backgroundSize: 'contain',
        backgroundRepeat: 'repeat'
      }, {
        content: ['I grew up between countries and learned to love diversity.'],
        type: 'TextSegment'
      }, {
        type: 'Spacer',
        width: '100%'
      }, {
        content: ['     Talking'],
        type: 'TextSegment'
      }, {
        content: ['FRENCH'],
        type: 'KnockoutSegment',
        backgroundUrl: 'images/french.svg',
        backgroundAttachment: 'scroll'
      }, {
        content: ['ENGLISH'],
        type: 'KnockoutSegment',
        backgroundUrl: 'images/english.svg'
      }, {
        content: ['&'],
        type: 'TextSegment'
      }, {
        content: ['ITALIAN'],
        type: 'KnockoutSegment',
        backgroundUrl: 'images/italian.svg',
        backgroundAttachment: 'scroll'
      }, {
        content: ['hardwired me into thinking'],
        type: 'TextSegment'
      }, {
        content: ['outside the box.'],
        type: 'KnockoutSegment',
        backgroundUrl: 'images/texture.gif',
        backgroundAttachment: 'fixed',
        backgroundSize: 'unset',
        backgroundRepeat: 'repeat'
      }, {
        type: 'Spacer',
        width: '100%'
      }, {
        content: ['I was born'],
        type: 'TextSegment'
      }, {
        content: ['color-blind.'],
        type: 'KnockoutSegment',
        backgroundUrl: 'images/colorblind.jpg'
      }, {
        content: ['For me'],
        width: '100%',
        type: 'TextSegment'
      }, {
        content: ['this'],
        type: 'ColorSegment',
        variant: 'one'
      }, {
        content: [' &'],
        type: 'TextSegment'
      }, {
        content: ['this'],
        type: 'ColorSegment',
        width: '100%',
        variant: 'two'
      }, {
        content: ['are the same colors.', 'This gave me a unique view on the world.'],
        type: 'TextSegment'
      }, {
        type: 'Spacer',
        width: '100%'
      }, {
        content: ['One of my dreams is to'],
        type: 'TextSegment'
      }, {
        content: ['fly to the moon.', 'contribute towards a more durable planet.', 'time-travel back to a concert of The Doors.'],
        type: 'SlideSegment',
        width: '100%'
      }, {
        type: 'Spacer',
        width: '100%'
      }, {
        content: ['My hobbies include'],
        type: 'TextSegment'
      }, {
        content: ['cooking.', 'sailing.', 'video-games.', 'coding.'],
        type: 'SlideSegment',
        width: '100%'
      }, {
        content: ['Overall I try to remain'],
        type: 'TextSegment'
      }, {
        content: ['curious.'],
        type: 'KnockoutSegment',
        backgroundUrl: 'images/curious.gif',
        backgroundAttachment: 'scroll',
        backgroundSize: '18vw 18vw',
        backgroundRepeat: 'repeat'
      }, {
        type: 'Spacer',
        width: '100%'
      }, {
        content: ['Currently crafting'],
        type: 'TextSegment'
      }, {
        content: ['the future of insurance', 'innovative tech', 'front-end awesomeness'],
        type: 'SlideSegment',
        width: '100%'
      }, {
        content: ['at '],
        type: 'TextSegment'
      }, {
        content: ['AXA.'],
        type: 'KnockoutSegment',
        backgroundColor: '#00008F'
      }, {
        type: 'Spacer',
        width: '100%'
      }, {
        content: ['Feel free to give me a shout!'],
        type: 'TextSegment'
      }, {
        type: 'SocialSegment',
        width: '100%'
      }]
    }
  }
}
</script>

<style>
:root {
  --text-size: 14vw;
}

body {
  font-family: -apple-system, system-ui, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  margin: 0;
  padding: 0;
  line-height: 1.5;
  background-color: black;
}
</style>
<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Raleway:wght@900&display=swap');

.layout {
  margin: 0 auto;
  padding-left: 20px;
  padding-right: 20px;
}

.logo-title {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: var(--text-size);
  background-repeat: no-repeat;
  background-color: black;
  overflow: hidden;

  .logo-effect {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    margin: auto;
    max-width: 512px;
    max-height: 512px;
  }

  .logo-container {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    background: black;
    mix-blend-mode: multiply;
  }
}

.segment-container {
  z-index: 1;
  margin-top: calc(100vh - var(--text-size));
  display: flex;
  flex-flow: row wrap;
  max-width: 100%;

  .segment {
    font-family: 'Raleway', sans-serif;
    font-size: var(--text-size);
    line-height: calc(var(--text-size) * 0.85);
    color: white;
    hyphens: none;
    word-break: normal;
    display: flex;
    flex-flow: row wrap;
    cursor: default;
    user-select: none;
    max-width: 100%;
  }
}
</style>
