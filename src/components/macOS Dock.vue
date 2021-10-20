<template>
  <div class="css-demo flex-ct-x" style="height:300px;" data-title="macOS Dock效果">
    <ul class="dock flex-ct-x" @mouseleave="resetScale" @click="handleClickGotoUrl">
      <li class="dock-item flex-ct-x" v-for="item in 12" :key="item" @mousemove="handleMousemove">
        <div class="app flex-ct-x">app{{item}}</div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  methods: {
    handleMousemove(e) {
      let item = e.target
      let itemRect = item.getBoundingClientRect()
      let offset = Math.abs(e.clientX - itemRect.left) / itemRect.width

      let prev = item.previousElementSibling || null,
          next = item.nextElementSibling || null
      let scale = 0.6

      this.resetScale()
      if (prev) {
        prev.style.setProperty('--scale', 1 + scale * Math.abs(offset - 1))
      }
      item.style.setProperty('--scale', 1 + scale)
      if (next) {
        next.style.setProperty('--scale', 1 + scale * offset)
      }
    },
    resetScale() {
      document.querySelectorAll('.dock li').forEach(li => {
        li.style.setProperty('--scale', 1)
      })
    },
    handleClickGotoUrl(e) {
      if (e.target.nodeName.toLowerCase() == 'li') {
        // todo
      }
    }
  }
}
</script>

<style lang="scss" scoped>
$color-list: #f66 #66f #f90 #09f #9c3 #3c9;

.dock {
  width: 100%;
  &-item {
    --scale: 1;
    padding: 0 10px;
    color: #fff;
    transition: 15ms all ease-out;
    cursor: pointer;
    .app {
      position: relative;
      top: calc((50px * var(--scale) - 50px) / 2 * -1);
      width: calc(50px * var(--scale));
      height: calc(50px * var(--scale));
      border-radius: 12px;
      pointer-events: none;
    }
  }
}

@each $color in $color-list {
  $index: index($color-list, $color);
  .dock-item:nth-child(#{$index}) .app{
    background-color: $color;
  }
  .dock-item:nth-child(#{$index + 6}) .app{
    background-color: $color;
  }
}
</style>