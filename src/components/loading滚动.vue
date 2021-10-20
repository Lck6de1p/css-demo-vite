<template>
  <div
    class="css-demo flex-ct-x"
    data-title="滚动loading"
    style="background-color: #0c0817; height: 300px;"
  >
    <div class="boxLoading"></div>
  </div>
</template>

<style lang="scss" scoped>
.boxLoading {
  position: relative;
  width: 50px;
  height: 50px;
  &::before {
    position: absolute;
    top: 59px;
    left: 0;
    width: 50px;
    height: 5px;
    background: #fff;
    opacity: 0.7;
    border-radius: 50%;
    content: "";
    animation: bottomMove 0.5s linear infinite;
  }
  &::after {
    position: absolute;
    top: 0;
    left: 0;
    width: 50px;
    height: 50px;
    background: #e04960;
    border-radius: 3px;
    content: "";
    animation: rotate 0.5s linear infinite;
  }
}

@keyframes rotate {
  25% {
    transform: translateY(9px) rotate(22.5deg);
  }
  50% {
    transform: translateY(18px) scale(1, 0.9) rotate(45deg);
    border-bottom-right-radius: 40px;
  }
  75% {
    transform: translateY(9px) rotate(67.5deg);
  }
  100% {
    transform: translateY(0) rotate(90deg);
  }
}
@keyframes bottomMove {
  0%,
  100% {
    transform: scale(1, 1);
  }
  50% {
    transform: scale(1.2, 1);
  }
}
</style>