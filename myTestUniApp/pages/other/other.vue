<template>
	<!-- v-bind:可以简写成: 组件属性要使用data中定义的数据变量，或者组件属性要是使用表达式-->
	<!-- v-on:可以简写成@ 绑带事件-->
	<!--  v-model 数据双向绑定 -->
	<!-- v-if条件判断,决定某个内容或区域是否挂载 -->
	<!-- v-show：条件判断，是否显示 -->
	<view v-bind:class="msg" :data="ture?'对的':'错的'">
		{{msg}}
		<button v-on:click="show">点我</button>
		<button @click="show">点我v-on:简写</button>
		<input class="msg-input" v-model="msg" />
		<view v-if="flag2 == 'Vue'">Vue</view>
		<view v-else-if="flag2 == 'CSS'">CSS</view>
		<view v-else>H5</view>
		
		<view v-if="flag"> if</view>
		<view v-show='flag'> show</view>
		<view>{{flag?'显示':'隐藏'}}</view>
		
		<!-- 空标签 -->
		<block v-if="!flag">
			<view>a</view>
			<view>b</view>
		</block>
		
		<view v-for="(item,index) in arr">{{index}}:{{item}}</view>
		<view v-for="(value,key) in person">{{key}}:{{value}}</view>
		
		<view v-for="item in persons">
			<view>姓名:{{item.name}}</view>
			<view>年龄:{{item.age}}</view>
		</view>
		
		
		
	</view>
	
</template>

<script>
	export default {
		//初始化数据
		data(){
			return{
				msg:'Hello',
				flag:true,
				flag2:'Vue',
				arr:['Vue','CSS','H5'],
				person:{
					name:'张三',
					age:18
				},
				persons:[
				{
					name:'李四',
					age:30
				},
				{
					name:'王武',
					age:20
				},
				{
					name:'赵四',
					age:19
				}]
				
			}
		},
		onLoad() {
			setTimeout(()=>{
				this.msg = this.msg + 'Tom'
				this.flag = !this.msg
				this.flag2 = 'CSS'
			},2000)
		},
		methods:{
			show(){
				console.log('点击了按钮')
			}
			
		},
		
	}
</script>

<style>
	.msg-input{
		border-radius: 8px;
		border-style:solid;
		border-width:1px;
		border-color: #4CD964;
	}
</style>
