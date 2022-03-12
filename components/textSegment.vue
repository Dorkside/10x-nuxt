<template>
  <span class="content-container">
    <template v-for="(contentPart, partIndex) of content">
      <span
        v-for="(word, wordIndex) in contentPart.split(' ')"
        :id="word"
        :key="`${partIndex}-${wordIndex}`"
        class="word"
        :class="variant"
      >
        <span
          v-for="(letter,index) in word"
          :key="index"
          class="letter"
          :style="{color}"
          :class="{letter, variant, uppercase: letter === letter.toUpperCase()}"
        >{{ letter }}</span>
        <span
          v-if="getLetterIndex(partIndex, wordIndex, word.length) !== contentPart.length"
          class="letter space"
        >&nbsp;</span>
      </span>
    </template>
  </span>
</template>
<script>
export default {
  name: 'TextSegment',
  props: {
    content: {
      type: Array,
      default: () => []
    },
    variant: {
      type: String,
      default: 'opacity'
    },
    color: {
      type: String,
      default: 'white'
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
  max-width: 100%;
  flex: auto;
}

.word {
  display: inline-block;

  &.opacity {
    opacity: 0.8;
  }

  transition: opacity 0.6s ease-in-out, color 0.8s ease-in-out;

  &:hover {
    opacity: 1;
  }

  .letter {
    &.uppercase {
      font-size: calc(var(--text-size) * 1.2);
      letter-spacing: calc(var(--text-size) * -0.1);
      margin-left: calc(var(--text-size) * -0.1);
    }

    &.space {
      letter-spacing: calc(var(--text-size) * -1);
    }

    &.opacity {
      opacity: 0.4;
    }

    transition: opacity 0.3s ease-in-out, color 0.8s ease-in-out;

    &:hover {
      opacity: 1;
      color: white;
    }
  }
}

#James {
  opacity: 1;
}
</style>
