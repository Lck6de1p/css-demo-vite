<template>
  <div class="flex-ct-x typing css-demo" data-title="打字机效果">
    <span>Hello CSS!</span>
  </div>
</template>

<style lang="scss" scoped>
.typing {
  height: 300px;
  span {
    display: inline-block;
    font: bold 200% Consolas, Monaco, monospace;   /*Monospaced font*/
    width: 10ch;
    font-weight: 500;
    color: #09f;
    overflow: hidden;
    white-space: nowrap;
    border-right: 1px solid transparent;
    animation: typing 3s steps(10) infinite, cursor .5s steps(1) infinite;
  }
}



@keyframes typing {
  from {
    width: 0;
  }
}

@keyframes cursor {
  50% {
    border-right-color: currentColor
  }
}
</style>