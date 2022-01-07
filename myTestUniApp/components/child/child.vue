<template>
	<view>
		<text>我是组件</text>
		<view>{{msg}}</view>
		<view>
			<button @click="sayHelloToFather">子向父组件传递数据</button>
		</view>
	</view>
</template>




<script>
	export default{
		props:['msg'],
		data(){
			return{
				
			};
		},
		methods:{
			sayHelloToFather(){
				console.log(uni.$u.config.v);
				this.$emit('childEvent','那笔小新')
				// uni.$emit('getInfo','樱桃小丸子')
			}
		}
	}
</script>

<style>
</style>
