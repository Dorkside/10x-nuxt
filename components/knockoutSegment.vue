<template>
  <span
    class="content-container"
  >
    <template v-for="(contentPart, partIndex) of content">
      <template v-for="(word, wordIndex) in contentPart.split(' ')">
        <span
          :id="word"
          :key="`${partIndex}-${wordIndex}`"
          class="word"
          :style="{
            backgroundImage: `url(${backgroundUrl})`,
            backgroundColor: `${backgroundColor}`,
            backgroundAttachment: `${backgroundAttachment}`,
            backgroundPosition: `${backgroundPosition}`,
            backgroundRepeat: `${backgroundRepeat}`,
            backgroundSize: `${backgroundSize}`,
          }"
        >
          <div
            class="bg"
          />
          <span
            v-for="(letter,index) in word"
            :key="index"
            class="letter"
            :class="{letter, uppercase: letter === letter.toUpperCase()}"
          >{{ letter }}</span>
        </span>
        <span
          v-if="getLetterIndex(partIndex, wordIndex, word.length) !== contentPart.length"
          :key="`${partIndex}-${wordIndex}-space`"
          class="letter space"
        >&nbsp;</span>
      </template>
    </template>
  </span>
</template>
<script>
export default {
  name: 'KnockoutSegment',
  props: {
    content: {
      type: Array,
      default: () => []
    },
    backgroundUrl: {
      type: String,
      default: ''
    },
    backgroundColor: {
      type: String,
      default: ''
    },
    backgroundAttachment: {
      type: String,
      default: 'fixed'
    },
    backgroundPosition: {
      type: String,
      default: 'center'
    },
    backgroundRepeat: {
      type: String,
      default: 'no-repeat'
    },
    backgroundSize: {
      type: String,
      default: 'cover'
    }
  },
  methods: {
    getLetterIndex (partIndex, wordIndex, letterIndex) {
      const words = this.content[partIndex].split(' ')
      let wordLetters = 0
      if (wordIndex > 0) {
        wordLetters = words.splice(0, wordIndex)
          .map(word => word.length)
          .reduce((sum, nbLetters) => sum + nbLetters, 0)
      }
      return wordLetters + wordIndex + letterIndex
    }
  }
}
</script>
<style lang="scss" scoped>
.content-container {
  z-index: -1;
  max-width: 100%;
}

.bg {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

.word {
  display: inline-block;
  transition: opacity 0.6s ease-in-out;
  color: white;
  background-position: center;
  position: relative;
  overflow: hidden;
  background-color: white;
  vertical-align: top;

  @media (max-width: 1024px) {
    background-attachment: scroll !important;
  }
}

.letter {
  background: black;
  transition: opacity 0.3s ease-in-out, color 0.8s ease-in-out;
  mix-blend-mode: multiply;

  &.space {
    letter-spacing: calc(var(--text-size) * -1);
  }

  &.uppercase {
    font-size: calc(var(--text-size) * 1.2);
    line-height: 0.8em;
  }
}
</style>
