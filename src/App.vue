<template>
  <div id="app">
    <vHeader />
    <component21 />
    <component1 />
    <component2 />
    <component3 />
    <component4 />
    <component5 />
    <component6 />
    <component7 />
    <component8 />
    <component9 />
    <component10 />
    <component11 />
    <component12 />
    <component13 />
    <component14 />
    <component15 />
    <component16 />
    <component17 />
    <component18 />
    <component19 />
    <component20 />
  </div>
</template>

<script>
import vHeader from '@/components/header.vue'
import component1 from '@/components/朋克风按钮.vue'
import component2 from '@/components/打字机效果.vue'
import component3 from '@/components/水球动画.vue'
import component4 from '@/components/橡皮擦效果.vue'
import component5 from '@/components/卡片集.vue'
import component6 from '@/components/手风琴效果.vue'
import component7 from '@/components/文字渐入效果.vue'
import component8 from '@/components/hover展示按钮边框动画.vue'
import component9 from '@/components/九宫格图片展示.vue'
import component10 from '@/components/hover划线指示.vue'
import component11 from '@/components/文字渐变背景色.vue'
import component12 from '@/components/hover控制鼠标跟随按钮.vue'
import component13 from '@/components/使用selection改变选中文字颜色.vue'
import component14 from '@/components/box-shadow实现腥红之月.vue'
import component15 from '@/components/倒影.vue'
import component16 from '@/components/伪类实现对话框效果.vue'
import component17 from '@/components/macOS Dock.vue'
import component18 from '@/components/点击生成爱心.vue'
import component19 from '@/components/伪类控制input样式.vue'
import component20 from '@/components/文本展开收起功能.vue'
import component21 from  '@/components/loading滚动.vue'
export default {
  components: {
    vHeader,
    component1,
    component2,
    component3,
    component4,
    component5,
    component6,
    component7,
    component8,
    component9,
    component10,
    component11,
    component12,
    component13,
    component14,
    component15,
    component16,
    component17,
    component18,
    component19,
    component20,
    component21,
  },
}
</script>
<style lang='scss'>
body, html, #app {
  width: 100%;
  height: 100%;
}
#app {
  overflow-y: auto;
  overflow-x: hidden;
}
::-webkit-scrollbar{
  width: 5px;
  height: 5px;
}
::-webkit-scrollbar-thumb{
  border-radius: 1em;
  background-color: rgba(50,50,50,.3);
}
::-webkit-scrollbar-track{
  border-radius: 1em;
  background-color: rgba(50,50,50,.1);
}
.css-demo {
  position: relative;
  border-top: 1px solid #ccc;
  &::after {
    content: attr(data-title);
    position: absolute;
    left: 50%;
    top: 0;
    padding: 0 12px;
    color: #fff;
    line-height: 30px;
    background-color: #1e9fff;
    border-radius: 0 0 5px 5px;
    transform: translateX(-50%);
  }
}
</style>

