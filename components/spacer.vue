<template>
  <div class="spacer" />
</template>
<script>
export default {
  name: 'Spacer'
}
</script>
<style lang="scss" scoped>
.spacer {
  &::before {
    content: '';
  }

  background-color: white;
  opacity: 0.05;
  width: 100%;
  height: calc(var(--text-size) / 10);
  margin: var(--text-size) 0;
}
</style>
