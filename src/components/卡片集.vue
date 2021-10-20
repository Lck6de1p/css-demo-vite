<template>
  <div class="flex-ct-x css-demo card-list-wrapper" data-title="卡片夹">
    <div class="scroll-box">
      <div class="mini-card-grid">
        <article class="mini-card" v-for="item in 15" :key="item">
          <time><strong>Article</strong>On Dec 10, 2020</time>
          <h3>this is a css demo</h3>
          <div class="tags">css</div>
          <div class="author">
            <img src="http://lck6de1p.com/static/img/5.jpg" alt="" class="author-img">
            <strong>奇魔猪</strong>
          </div>
        </article> 
      </div>
    </div>
  </div>
  

</template>

<style lang="scss" scoped>
.ard-list-wrapper {
  height: 600px;
}
.scroll-box {
  position: relative;
  width: 800px; 
  margin: 100px auto;
  &::after {
    content: "";
    position: absolute;
    right: 0;
    top: 15px;
    bottom: 15px;
    width: 5px;
    border-radius: 5px;
    background: linear-gradient(130deg,#ff7a18,#af002d 41.07%,#319197 76.05%);
    box-shadow: -10px 0 20px 3px #000;
  }
}
.mini-card-grid {
  display: flex;
  padding: 30px 0 30px 20px;
  overflow-x: scroll;
  .mini-card {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    flex-shrink: 0;
    width: 300px;
    height: 350px;
    padding: 15px;
    border-radius: 16px;
    background: linear-gradient(85deg,#434343,#262626);
    box-shadow: -20px 0 30px -20px #000;
    color: #fff;
    transition: .2s;
    &:not(:first-child) {
      margin-left: -130px;
    }
    &:first-child:hover{
      transform: translate(-5px,-10px) rotate(3deg);
    }
    &:hover {
      transform: translateY(-10px) rotate(3deg);
    }
    &:hover~.mini-card {
      transform: translateX(130px);
    }
    time {
      color: #777;
      height: 30px;
    }
    h3 {
      height: 20px;
    }
    .tags {
      flex: 1;
      color: #ff7a18;
    }
  }
}

.author {
  display: flex;
  align-items: center;
  .author-img {
    width: 50px;
    height: 50px;
    margin-right: 15px;
    border-radius: 100%;
  }
}

// .mini-card-grid::-webkit-scrollbar-thumb {
//   background: #434343;
//   border-radius: 10px;
//   box-shadow: inset 2px 2px 2px hsla(0,0%,100%,.25), inset -2px -2px 2px rgba(0,0,0,.25);
// }
// .mini-card-grid::-webkit-scrollbar {
//   width: 10px;
//   height: 10px;
// }
</style>