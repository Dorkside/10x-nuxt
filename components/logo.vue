<template>
  <div class="outer-frame">
    <div class="frame">
      <div class="central gradient one" />
      <div class="central gradient two" />
      <div class="central gradient three" />
      <div class="central spot" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'Logo'
}
</script>

<style lang="scss" scoped>
.outer-frame {
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  height: 100vh;
  width: 100vw;
}

.frame {
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  margin: auto;
  width: 600px;
  max-width: 60vw;
  aspect-ratio: 1;
  border-radius: 16px 0;
  overflow: hidden;
}

@keyframes grow {
  from {
    opacity: 1;
    transform: scale(0);
  }

  to {
    opacity: 0;
    transform: scale(2);
  }
}

@keyframes grow-2 {
  from {
    opacity: 0;
    transform: scale(0);
  }

  to {
    opacity: 0.5;
    transform: scale(2);
  }
}

.central {
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  margin: auto;

  &.gradient {
    transform: scale(0.2);
    border-radius: 50%;
    animation-duration: 7s;
    animation-iteration-count: infinite;

    &.one {
      animation-name: grow;
      background: radial-gradient(hsla(0, 0, 0, 0) 0%, hsla(0, 0, 0, 50%) 30%, hsla(0, 0, 80%, 1) 70%, hsla(0, 0, 100%, 1) 80%, hsla(0, 0, 0, 50%) 100%);
    }

    &.two {
      animation-name: grow-2;
      background: radial-gradient(hsla(0, 0, 0, 0) 0%, hsla(0, 0, 0, 50%) 50%, hsla(0, 0, 100%, 1) 65%, hsla(0, 0, 100%, 1) 80%, hsla(0, 0, 0, 50%) 100%);
    }

    &.three {
      animation-name: grow;
      background: radial-gradient(hsla(0, 0, 0, 0) 0%, hsla(0, 0, 0, 50%) 10%, hsla(0, 0, 80%, 1) 50%, hsla(0, 0, 100%, 1) 80%, hsla(0, 0, 0, 50%) 100%);
    }
  }

  &.spot {
    background: black;
    width: calc(100% / (1.618 * 1.618));
    height: calc(100% / (1.618 * 1.618));

    &::after {
      content: "";
      position: absolute;
      top: 0;
      left: 0;
      background: black;
      height: calc(100% / (1.618 * 1.618));
      width: 100%;
      transform: translateX(-100%);
    }
  }
}
</style>
