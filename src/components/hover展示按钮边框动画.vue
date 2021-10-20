<template>
  <div class="flex-ct-x css-demo hover-button-animation-wrapper" data-title="hover展示按钮边框动画">
    <div class="button">CSS</div>
  </div>
</template>

<style lang="scss" scoped>
$color: #66f;
$bg: linear-gradient($color, $color);
.hover-button-animation-wrapper {
  height: 300px;
  .button {
    width: 200px;
    height: 80px;
    background: $bg no-repeat left top/0 2px,
      $bg no-repeat right top/2px 0,
      $bg no-repeat right bottom/0 2px,
      $bg no-repeat left bottom/2px 0;
      // background: [image] [repeat] [positon]/[size]
    cursor: pointer;
    line-height: 80px;
    text-align: center;
    font-size: 50px;
    font-weight: 700;
    color: $color;
    transition: all 300ms;
    &:hover {
      background-size: 100% 2px, 2px 100%, 100% 2px, 2px 100%;
    }
  }
}


</style>