<template>
  <div class="css-demo" data-title="使用selection控制选中文字的颜色">
    <div class="selection-wrapper flex-ct-x">
      <p>默认选中文字的颜色</p>
      <p class="special">使用selection控制选中文字的颜色</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.selection-wrapper {
  height: 300px;
  line-height: 40px;
  font-size: 18px;
  flex-direction: column;
  .special::selection {
    background-color: #42b983;
  }
}
</style>