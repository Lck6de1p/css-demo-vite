<template>
  <div class="css-demo" data-title=":out-of-range控制输入值是否在范围内">
    <div class="input-wrapper flex-ct-x">
      {{msg}}
      <input type="number" max="10" min="0" v-model="value1" class="self-input">
      <input type="number" max="10" min="0" v-model="value2" class="self-input">
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      msg: ' 允许范围<0-10>',
      value1: 11,
      value2: 10
      
    }
  }
}
</script>
<style lang="scss" scoped>
.input-wrapper {
  height: 300px;
  flex-direction: column;
  font-weight: bold;
  color: #66f;
  .self-input {
    display: inline-block;
    width: 200px;
    height: 40px;
    padding: 0 15px;
    border-radius: 4px;
    border: 1px solid #dcdfe6;
    margin-top: 20px;
    background-color: #fff;
    background-image: none;
    color: #606266;
    font-size: inherit;
    line-height: 40px;
    outline: none;
    &:in-range {
      border: 1px solid #dcdfe6;
    }
    &:out-of-range {
      border: 1px solid #ee0000;
    } 
  }
}
</style>