<template>
  <div class="css-demo" data-title="box-shadow实现腥红之月">
    <div class="flex-ct-x" style="height: 300px;">
      <div class="scarlet-moon-wrapper flex-ct-x">
        <div class="scarlet-moon"></div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.scarlet-moon-wrapper {
  width: 200px;
  height: 200px;
  background: #000;
  .scarlet-moon {
    position: relative;
    width: 100px;
    height: 100px;
    background: #000;
    border-radius: 50%;
    box-shadow: inset 10px 10px crimson;
    &::before,
    &::after {
      position: absolute;
      content: '';
      width: 100%;
      height: 100%;
      background: inherit;
      border-radius: inherit;
      box-shadow: inherit;
    }
    &::before {
      filter: blur(5px);
    }
    &::after {
      filter: blur(10px);
    }
  }

}
</style>