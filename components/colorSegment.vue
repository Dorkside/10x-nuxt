<template>
  <span class="content-container">
    <template v-for="(contentPart, partIndex) of content">
      <span
        v-for="(word, wordIndex) in contentPart.split(' ')"
        :id="word"
        :key="`${partIndex}-${wordIndex}`"
        class="word"
        :class="`${variant}`"
      >
        <span
          v-for="(letter,index) in word"
          :key="index"
          class="letter"
          :class="`${letter}`"
        >{{ letter }}</span>
      </span>
    </template>
  </span>
</template>
<script>
export default {
  name: 'ColorSegment',
  props: {
    content: {
      type: Array,
      default: () => []
    },
    variant: {
      type: String,
      default: 'one'
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

  &.one {
    :nth-child(1) {
      color: hsl(0, 60%, 25%);
    }

    :nth-child(2) {
      color: hsl(270, 100%, 40%);
    }

    :nth-child(3) {
      color: hsl(96, 100%, 50%);
    }

    :nth-child(4) {
      color: hsl(350, 100%, 87%);
    }
  }

  &.two {
    :nth-child(1) {
      color: hsl(0, 50%, 25%);
    }

    :nth-child(2) {
      color: hsl(240, 100%, 40%);
    }

    :nth-child(3) {
      color: hsl(60, 100%, 50%);
    }

    :nth-child(4) {
      color: hsl(0, 0%, 80%);
    }
  }
}

#James {
  opacity: 1;
}
</style>
