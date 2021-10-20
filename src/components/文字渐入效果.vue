<template>
  <div class="css-demo" data-title="文字随滚轮渐入效果">
    <div class="moving-wrapper">
      <div class="scroll-wrapper">
        <div class="sticky">
          <h1 id="move-text" style="--percentage: 0%;">Less bezel, more screen.</h1>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    const h1 = document.querySelector('#move-text')
    const box = document.querySelector('.moving-wrapper')
    box.addEventListener('scroll', () => {
      let scrolled = box.scrollTop / (box.scrollHeight - box.clientHeight)
      h1.style = `--percentage:${scrolled * 100}%`
    })
  }
}
</script>

<style lang="scss" scoped>
.moving-wrapper {
  height: 300px;
  background-color: #fff;
  overflow-y: auto;
  .scroll-wrapper {
    height: 1000px;
  }
}
h1 {
  font-family: Helvetica;
  margin: 0;
  padding: 0;
  font-size: 48px;
  color: #000;
  letter-spacing: -0.3px;
  background-image: linear-gradient(75deg, rgba(0,0,0,1) 0%,
  rgba(0,0,0,1) 33.33%, rgba(0,0,0,0) 66.67%,
  rgba(0,0,0,0) 100%);  
  background-size: 300% 100%;
  background-position-x: calc(100% - var(--percentage));
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
}
.sticky {
  position: sticky;
  top: 0;
  height: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>