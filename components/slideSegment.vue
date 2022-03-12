<template>
  <span class="content-container">
    <template
      v-for="(contentPart, partIndex) of content"
    >
      <span
        v-for="(word, wordIndex) in contentPart.split(' ')"
        :id="word"
        :key="`${partIndex}-${wordIndex}`"
        class="word"
        :class="{current: partIndex === currentPart}"
      >
        <span
          v-for="(letter, letterIndex) in word"
          :key="letterIndex"
          class="letter"
          :class="{current: getLetterIndex(partIndex, wordIndex, letterIndex) <= currentLetter}"
        >
          {{ letter }}
        </span>
        <span
          v-if="getLetterIndex(partIndex, wordIndex, word.length) !== contentPart.length"
          class="letter space"
          :class="{current: getLetterIndex(partIndex, wordIndex, word.length) <= currentLetter}"
        >&nbsp;</span>
      </span>
    </template>
    <span class="spacer" />
  </span>
</template>
<script>
export default {
  name: 'SlideSegment',
  props: {
    content: {
      type: Array,
      default: () => []
    }
  },
  data () {
    return {
      currentPart: 0,
      currentLetter: 0
    }
  },
  mounted () {
    this.addLetter()
  },
  methods: {
    addLetter () {
      setTimeout(() => {
        this.currentLetter += 1
        if (this.currentLetter === this.content[this.currentPart].length) {
          setTimeout(() => {
            this.currentPart += 1
            this.currentPart %= this.content.length
            this.currentLetter = 0
            this.addLetter()
          }, 1000)
        } else {
          this.addLetter()
        }
      }, Math.random() * 300 + 120)
    },
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
  white-space: nowrap;
  display: flex;
  flex-flow: row nowrap;
  justify-content: flex-end;
}

.word {
  flex-grow: 0;
  flex-shrink: 0;
  display: none;
  opacity: 0.8;
  transition: opacity 0.6s ease-in-out;
  margin-right: 8px;

  &.current {
    display: inline-block;
  }

  &:hover {
    opacity: 1;
  }
}

.letter {
  display: none;
  opacity: 0.4;
  transition: opacity 0.3s ease-in-out, color 0.8s ease-in-out;
  font-family: 'Rubik Mono One', Consolas, monospace;

  &.space {
    letter-spacing: calc(var(--text-size) * -1);
  }

  &.current {
    display: inline-block;
  }

  &:hover {
    opacity: 1;
  }
}

.spacer {
  margin-left: -12px;
  border-left: solid calc(var(--text-size) / 10) transparent;
  flex-grow: 1;
  flex-shrink: 1;
  animation: blink 1s;
  animation-iteration-count: infinite;
  transition: none;
}

@keyframes blink { 50% { border-color: #fff; } }
</style>
