<template>
	<view>
		<!--
		使用easycom规范（components 目录下创建目录，组件名通组件目录名），可以直接使用组件
		 父组件向子组件传递数据用 props
		 子组件向父组件传递数据可以通过 自定义事件 父组件自定义事件 子组件触发父组件定义的事件，并传递数据
		 子组件可以定义插槽 让父组件自定义要显示的内容
		 -->
		<view @click="show"></view>
		<view @click="flag = !flag">点击改变flag</view>
		<view v-if="flag"> show flag</view>
		
		<view @click="c1">
			我是父级
			<view @click.stop="c2">我自子级</view>
		</view>
		
		<scroll-view class="scroll" :scroll-y="true"  @scroll="scroll">
			<view v-for="i in 100">111</view>
		</scroll-view>
		<card color="red" size="18px">红色</card>
		<card color="blue">蓝色</card>
		<!-- #ifndef APP-PLUS -->
		<card @myClick='myClick'>黄色</card>
		<!-- #endif -->
		<view class="bg-clor">
			<view>11111</view>
			<view class="text">22222</view>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				flag:false
				
			}
		},
		onLoad() {
			
		},
		methods:{
			show(){
				console.log('点击了')
			},
			c1(){
				console.log('点父级')
			},
			c2(){
				console.log('点击子级')
			},
			scroll(event){
				console.log(event)
			},
			myClick(msg){
				//#ifdef MP
				console.log('父组件的自定义事件' + msg)
				//#endif
			}
		}
	}
</script>

<style lang="scss" scoped>
@import  './about.css';
	.scroll{
		height: 400rpx;
	}
	.bg-clor{
		background-color: #007AFF;
		.text {
			color: red;
		}
	}
</style>
