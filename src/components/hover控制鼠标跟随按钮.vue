<template>
  <div class="css-demo flex-ct-x" data-title="hover控制鼠标跟随按钮" style="height: 300px">
    <div class="hover-follow-btn" @mousemove="move" @click="handleClick">
      <span>Hello Scss</span>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    move(e) {
      e.target.style.setProperty('--x', `${e.offsetX}px`)
      e.target.style.setProperty('--y', `${e.offsetY}px`)
    },
    handleClick() {
      console.log('click!')
    }
  }
}
</script>

<style lang="scss" scoped>
.hover-follow-btn {
  position: relative;
  width: 300px;
  height: 50px;
  border-radius: 25px;
  font-size: 20px;
  font-weight: bold;
  line-height: 50px;
  text-align: center;
  color: #fff;
  background: #66f;
  cursor: pointer;
  overflow: hidden;
  span {
    position: relative;   // 防止文字被伪类背景盖住
		pointer-events: none; // 防止鼠标移动到文字上导致动画失效造成卡顿的感觉
	}
  &::before {
    content: '';
    position: absolute;
    left: var(--x);
    top: var(--y);
    width: 0;
		height: 0;
    background-image: radial-gradient(circle closest-side, #09f, transparent);
    transform: translate3d(-50%, -50%, 0);
    transition: width 200ms ease, height 200ms ease;
  }
  &:hover::before {
    width: 400px;
		height: 400px;
  }
}
</style>