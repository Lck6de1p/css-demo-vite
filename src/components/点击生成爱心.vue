<template>
  <div class="css-demo" data-title="点击生成爱心">
    <div class="heart-wrapper flex-ct-x" @click="handleClick">
      试着点击此区域
      <div
        class="heart-box"
        v-for="item in heartList"
        :key="item.id"
        :style="{ '--x': item.x, '--y': item.y }"
      >
        <div class="heart" :style="{ '--color': item.color }"></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const colorList = ["#f66", "#66f", "#f90", "#09f", "#9c3", "#3c9"];
const heartList = ref([]);
const count = ref(0);

function handleClick(e) {
  console.log(1)
  heartList.value.push({
    id: count.value++,
    x: e.offsetX - 10 + "px",
    y: e.offsetY - 10 + "px",
    color: colorList[count.value % 6],
  });
  setTimeout(() => {
    heartList.value.shift();
  }, 2100);
}
</script>

<style lang="scss" scoped>
$width: 15px;

.heart-wrapper {
  height: 300px;
  position: relative;
  letter-spacing: 1ch;
  font-weight: bold;
  color: #66f;
  .heart-box {
    position: absolute;
    top: calc(var(--y));
    left: calc(var(--x));
    width: $width;
    height: $width;
    pointer-events: none;
    .heart {
      position: relative;
      width: $width;
      height: $width;
      background: var(--color);
      border-radius: 0 0 2px 0;
      animation: move 2000ms forwards;
      &::before,
      &::after {
        content: "";
        position: absolute;
        background: var(--color);
        width: $width;
        height: $width;
        border-radius: 100%;
      }
      &::before {
        left: -10px;
        top: 0;
      }
      &::after {
        top: -10px;
        left: 0;
      }
    }
  }
}

@keyframes move {
  0% {
    opacity: 0.8;
    transform: translateY(0px) rotate(45deg);
  }
  100% {
    opacity: 0;
    transform: translateY(-50px) rotate(45deg);
  }
}
</style>