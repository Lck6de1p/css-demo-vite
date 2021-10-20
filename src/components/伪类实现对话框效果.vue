<template>
  <div class="css-demo" data-title="伪类实现对话框效果">
    <div class="dialog">
      <div 
        v-for="(msg, index) in msgList" 
        class='msg-wrapper'
        :class="{'msg-wrapper-left': msg.type=='left', 'msg-wrapper-right': msg.type=='right'}"
        :key="index">
        <div 
          class="msg-item" 
          :class="{'msg-item-left': msg.type=='left', 'msg-item-right': msg.type=='right'}">
          {{msg.value}}
        </div>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      msgList: [
        {value: 'Hello! vue!', type: 'left'},
        {value: 'Hi! scss!', type: 'right'},
        {value: 'Bye!', type: 'left'},
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
.dialog {
  width: 300px;
  height: 400px;
  padding-top: 10px;
  margin: 100px auto;
  background: #f1f1f1;
  overflow: auto;
}
.msg-wrapper {
  display: flex;
  padding: 0 20px;
  margin-bottom: 20px;
  &-left {
    justify-content: flex-start;
  }
  &-right {
    justify-content: flex-end;
  }
}
.msg-item {
  position: relative;
  display: inline-block;
  padding: 12px;
  border-radius: 4px;
  line-height: 20px;
  &-left {
    background: #fff;
    &::after {
      content: "";
      position: absolute;
      left: -20px;
      top: calc(50% - 10px);
      border: 10px solid transparent;
      border-right: 10px solid #fff;
    }
  }
  &-right {
    background: #8cb923;
    &::after {
      content: "";
      position: absolute;
      right: -20px;
      top: calc(50% - 10px);
      border: 10px solid transparent;
      border-left: 10px solid #8cb923;
    }
  }
}


</style>
