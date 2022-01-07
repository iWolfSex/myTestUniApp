<template>
	<view :style="{background:color,fontSize:size}" @click="handleClick">
		<slot></slot>
	</view>
</template>

<script>
	export default {
		name:'card',
		props:{
			color:{
				type:String,
				default:'yellow'
			},
			size:{
				type:String,
				default:'14px'
			}
		},
		data(){
			return{
				
			}
		},
		methods:{
			handleClick(){
				console.log('点击了自定义组件')
				this.$emit('myClick','这个数据来自子组件')
			}
		}
		
	}
</script>

<style>
</style>
