<template>
  <div class="css-demo" data-title="文本“展开收起”功能" style="height: 300px;">
    <div class="ellipsis-wrapper">
      <input type="checkbox" id="exp" class="exp">
      <div class="text">
        <label for="exp" class="btn"></label>
        例如， 罗马数字 2 写做 II ，即为两个并列的 1。12 写做 XII ，即为 X + II 。 27 写做  XXVII, 即为 XX + V + II 。

        通常情况下，罗马数字中小的数字在大的数字的右边。但也存在特例，例如 4 不写做 IIII，而是 IV。数字 1 在数字 5 的左边，所表示的数等于大数 5 减小数 1 得到的数值 4 。同样地，数字 9 表示为 IX。这个特殊的规则只适用于以下六种情况：

        I 可以放在 V (5) 和 X (10) 的左边，来表示 4 和 9。
        X 可以放在 L (50) 和 C (100) 的左边，来表示 40 和 90。 
        C 可以放在 D (500) 和 M (1000) 的左边，来表示 400 和 900。
        给你一个整数，将其转为罗马数字。w yiqi
      </div>
    </div>
  </div>
</template>

<script>
export default {

}
</script>
<style lang="scss" scoped>
.ellipsis-wrapper {  
  display: flex;
  width: 600px;
  padding: 15px ;
  margin: 50px auto;
  border-radius: 8px;
  box-shadow: 20px 20px 60px #bebebe,
    -20px -20px 60px #ffffff;
  .text {
    position: relative;
    font-size: 16px;
    text-align: justify;
    text-overflow: ellipsis;
    text-indent: 2em;
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
    overflow: hidden;
    &::before {
      content: '';
      height: calc(100% - 24px);
      float: right;
    }
  }
  .exp {
    display: none;
  }
  .btn {
    padding: 0 8px;
    margin-left: 10px;
    border-radius: 4px;
    line-height: 24px;
    text-indent: 0; 
    background-color: #66f;
    float: right;
    clear: both;
    &::before {
      cursor: pointer;
      content: '展开'
    }
  }
  .exp:checked+.text {
    -webkit-line-clamp: 999;
    .btn::before {
      content: '收起'
    }
  }
  
}
</style>