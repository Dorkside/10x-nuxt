<template>
  <div class="outer-frame">
    <div class="frame">
      <div class="central gradient one" />
      <div class="central gradient two" />
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
  width: 300px;
  height: 300px;
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
    animation-name: grow;
    animation-duration: 7s;
    animation-iteration-count: infinite;
    border: solid 2px white;

    &.one {
      background: radial-gradient(hsla(0, 0, 0, 1) 0%, hsla(0, 0, 0, 1) 30%, hsla(0, 0, 80%, 1) 70%, hsla(0, 0, 100%, 1) 100%);
    }

    &.two {
      background: radial-gradient(hsla(0, 0, 0, 1) 0%, hsla(0, 0, 0, 1) 10%, hsla(0, 0, 80%, 1) 50%, hsla(0, 0, 100%, 1) 100%);
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
