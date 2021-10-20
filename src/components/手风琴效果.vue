<template>
  <div class="flex-ct-x css-demo accordion-wrapper" data-title="手风琴效果">
    <ul class="accordion">
      <li class="item" v-for="item in 6" :key="item"></li>
    </ul>
  </div>
</template>
<style lang="scss" scoped>
.accordion-wrapper {
  height: 300px;
}
.accordion {
  display: flex;
  width: 600px;
  height: 200px;
  .item {
    flex: 1;
    height: 100%;
    transition: all 300ms;
    &:nth-child(1) {
      background-color: #f66;
    }
    &:nth-child(2) {
      background-color: #66f;
    }
    &:nth-child(3) {
      background-color: #f90;
    }
    &:nth-child(4) {
      background-color: #09f;
    }
    &:nth-child(5) {
      background-color: #9c3;
    }
    &:nth-child(6) {
      background-color: #3c9;
    }
    &:hover {
    flex: 2;
    }
  }
}
</style>