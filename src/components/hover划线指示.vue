<template>
  <div class="flex-ct-x css-demo" data-title="hover划线跟随指示" style="height: 300px">
    <ul class="underline-nav">
      <li v-for="item in 6" :key="item">nav标题{{item}}</li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
$color: #66f;
.underline-nav {
  display: flex;
  li {
		position: relative;
		padding: 10px;
		cursor: pointer;
		font-size: 20px;
		color: $color;
		transition: all 300ms;
		&::before {
      content: "";
			position: absolute;
			left: 100%;
			top: 0;
			width: 0;
			height: 100%;
      border-bottom: 2px solid transparent;
			transition: all 300ms;
		}
		&:active {
			background-color: $color;
			color: #fff;
		}
		&:hover {
			&::before {
				left: 0;
				top: 0;
        width: 100%;
				border-bottom-color: $color;
        z-index: -1;
				transition-delay: 100ms;
			}
			& + li::before {
				left: 0;
			}
		}
	}
}
</style>