<template>
  <div class="flex-ct-x state-ball-wrapper css-demo" data-title="水球动画">
    <div class="state-ball" style="--offset: 0;">
      <div class="wave"></div>
      <div class="progress"></div>
    </div>
  </div>
</template>

<script>
export default {
  mounted() {
    this.move()
  },
  methods: {
    move() {
      let box = document.getElementsByClassName('state-ball')[0];
      let progress = 0;
      let trendIsUp = true;
      setInterval(() => {
        if (trendIsUp) {
          if (progress < 100) {
            progress++;
          } else {
            trendIsUp = false;
          }
        } else {
          if (progress > 0) {
            progress--;
          } else {
            trendIsUp = true;
          }
        }
        box.style = `--offset: ${progress}`;
      }, 100)
    }
  }
}
</script>

<style lang="scss" scoped>
.state-ball-wrapper {
  height: 300px;
}
.state-ball {
  position: relative;
  width: 150px;
  height: 150px;
  padding: 5px;
  border: 3px solid #3c9;
  border-radius: 100%;
  background-color: #fff;
  overflow: hidden;
}
.state-ball::before,
.state-ball::after {
  content: '';
  position: absolute;
  left: 50%;
  bottom: 5px;
  z-index: 9;
  width: 200px;
  height: 200px;
  margin-left: -100px;
}
.state-ball::before {
  margin-bottom: calc(var(--offset) * 1.34px);
  border-radius: 45%;
  background-color:rgba(255,255,255, .5);
  animation: rotate 10s linear -5s infinite;
}
.state-ball::after {
  margin-bottom: calc(var(--offset) * 1.34px + 10px);
  border-radius: 40%;
  background-color:rgba(255,255,255, .8);
  animation: rotate 15s infinite;
}
@keyframes rotate {
  to {
      transform: rotate(1turn)
  }
}

.wave {
  position: relative;
  width: 100%;
  height: 100%;
  border-radius: 100%;
  background-image: linear-gradient(to bottom, #af8 13%, #3c9 91%)
}

.progress::after {
  content: counter(progress) "%";
  counter-reset: progress var(--offset);
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  font-weight: bold;
  font-size: 16px;
  color: #09f;
  z-index: 99;
}
</style>
