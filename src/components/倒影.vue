<template>
  <div class="css-demo" data-title="分别用-webkit-box-reflect和伪类实现倒影">
    <div class="reflect-wrapper">
      <div class="reflect"></div>
      <div class="before"></div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.reflect-wrapper {
  display: flex;
  justify-content: space-around;
  height: 500px;
  padding: 0 200px;
  margin-top: 100px;
  .reflect {
    width: 150px;
    height: 150px;
    background-image: url('http://lck6de1p.com/static/img/2.jpg');
    background-size: contain;
    -webkit-box-reflect: below 10px linear-gradient(transparent, rgba(0,0,0,.5))
  }
  .before {
    position: relative;
    width: 150px;
    height: 150px;
    background-image: url('http://lck6de1p.com/static/img/3.jpg');
    background-size: contain;
    &::before {
      content: '';
      position: absolute;
      left: 0;
      bottom: calc(-100% - 10px);
      width: 100%;
      height: 100%;
      background-image: inherit;
      background-size: inherit;
      transform: rotateX(180deg);
    }
    &::after {
      content: "";
      position: absolute;
      left: 0;
      bottom: calc(-100% - 10px);
      width: 100%;
      height: 100%;
      background: linear-gradient(0deg, rgba(255, 255, 255, .9)0%, rgba(255, 255, 255, .6)100%);
      z-index: 2;
    }
  }
}
</style>