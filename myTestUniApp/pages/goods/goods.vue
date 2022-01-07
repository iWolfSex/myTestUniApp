<template>
<view>商品</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		components:{
		},
		onLoad() {
			uni.$on('getInfo',name =>{
				//consle.log('Me 页面中的全局事件被触发了')
				this.name = name
			})
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
