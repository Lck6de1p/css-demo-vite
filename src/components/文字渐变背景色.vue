<template>
  <div class="flex-ct-x css-demo" data-title="文字渐变背景色" style="height:300px">
    <div class="background-gradient-wrapper">
      Hello Scss!
    </div>

  </div>
</template>

<script>
export default {

}
</script>
<style lang="scss" scoped>
.background-gradient-wrapper {
  height: 60px;
  font-size: 50px;
  color: transparent;
  background: linear-gradient(45deg, #228DFD 20%, #00CF00 40%, #F45749 80%);
  background-clip: text;
}
</style>