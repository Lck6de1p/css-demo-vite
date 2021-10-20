<template>
  <div class="flex-ct-x css-demo pic9-wrapper" data-title="九宫格图片展示">
    <p>我也不知道猪圈里为什么会多了些奇怪的东西</p>
    <div class="album">
      <img
        v-for="(item, index) in imgShowList"
        :key="index"
        :src="item"
        alt=""
      />
    </div>
  </div>
</template>

<script setup>
import { ref, computed, onMounted } from "vue";
const imgList = ref([
  "http://lck6de1p.com/static/img/7.jpg",
  "http://lck6de1p.com/static/img/1.jpg",
  "http://lck6de1p.com/static/img/2.jpg",
  "http://lck6de1p.com/static/img/3.jpg",
  "http://lck6de1p.com/static/img/4.jpg",
  "http://lck6de1p.com/static/img/5.jpg",
  "http://lck6de1p.com/static/img/6.jpg",
  "http://lck6de1p.com/static/img/8.jpg",
  "http://lck6de1p.com/static/img/1.jpg",
]);
const count = ref(9);
const isAdd = ref(false);

const imgShowList = computed(() => imgList.value.slice(0, count.value));

console.log(imgList.value.slice(0, count.value));

onMounted(() => {
  setInterval(() => {
    if (isAdd.value) {
      count.value++;
      if (count.value == 9) {
        isAdd.value = false;
      }
    } else {
      count.value--;
      if (count.value == 1) {
        isAdd.value = true;
      }
    }
  }, 1000);
});
</script>
<style lang="scss" scoped>
.pic9-wrapper {
  font-weight: bold;
  color: #66f;
  flex-direction: column;
  height: 500px;
  p {
    margin-bottom: 12px;
  }
  .album {
    width: 342px;
    height: 342px;
    img {
      display: inline-block;
      margin: 0 3px 3px 0;
      width: 110px;
      height: 110px;
      &:only-child {
        width: initial;
        height: initial;
        max-width: 230px;
        max-height: 230px;
      }
      &:nth-child(2):nth-last-child(3) {
        margin-right: 110px;
      }
    }
  }
}
</style>