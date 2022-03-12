<template>
  <span class="content-container">
    <a :href="url" target="_blank">
      <span
        v-for="(word, wordIndex) in text.split(' ')"
        :id="word"
        :key="`${wordIndex}`"
        class="word"
        :class="variant"
      >
        <span
          v-for="(letter,index) in word"
          :key="index"
          class="letter"
          :class="`${letter} ${variant}`"
          :style="{color}"
        >{{ letter }}</span>
        <span
          v-if="getLetterIndex(wordIndex, word.length) !== text.length"
          class="letter space"
        >&nbsp;</span>
      </span>
    </a>
  </span>
</template>
<script>
export default {
  name: 'LinkSegment',
  props: {
    text: {
      type: String,
      default: undefined
    },
    url: {
      type: String,
      default: undefined
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
    getLetterIndex (wordIndex, letterIndex) {
      const words = this.text.split(' ')
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
  position: relative;
}

a::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: calc(var(--text-size) / 5);
  background: black;
  opacity: 0;
  transition: opacity 0.3s ease-in-out, transform 0.3s ease-in-out;
  transform: scaleX(0);
  transform-origin: left center;
}

a:hover::after {
  opacity: 0.5;
  transform: scaleX(1);
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
}

.letter {
  &.opacity {
    opacity: 0.4;
  }

  &.space {
    letter-spacing: calc(var(--text-size) * -1);
  }

  transition: opacity 0.3s ease-in-out, color 0.8s ease-in-out;

  &:hover {
    opacity: 1;
    color: white;
  }
}

#James {
  opacity: 1;
}
</style>
