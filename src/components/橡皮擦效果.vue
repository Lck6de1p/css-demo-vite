<template>
  <div class="flex-ct-x css-demo eraser-wrapper" data-title="橡皮擦效果">
    <p>Hello CSS!</p>
    <div class="card">
      <div class="snow" v-for="item in 100" :key="item"></div>
    </div>
  </div>
</template>

<script>

</script>

<style lang="scss" scoped>

.eraser-wrapper {
  height: 100vh;
}

.card {
  $snow-size: 3em;
  width: $snow-size * 10;
  height: $snow-size * 10;
  display: flex;
  flex-wrap: wrap;
  background: #fff;
  filter: blur(15px) contrast(30);
  .snow {
    position: relative;
    width: $snow-size;
    height: $snow-size;
    border-radius: 100%;
    &::after {
      position: absolute;
      content: "";
      left: 0;
      width: inherit;
      height: inherit;
      background: #000;
      transition: 30s cubic-bezier(0.19, 1, 0.22, 1);
    }
    &:hover::after {
      transform: scale(0);
      transition-duration: .1s;
    }
  }
}

p {
  position: absolute;
  top: 50%;
  left: 50%;
  z-index: 9999;
  font-size: 4em;
  line-height: 1em;
  letter-spacing: 0.1em;
  transform: translate(-50%, -50%);
  pointer-events: none;
  filter: blur(1px) contrast(200);
}
</style>