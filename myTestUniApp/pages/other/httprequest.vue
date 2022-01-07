<template>
	<view>
		<view>
			{{vuex_name}}
		</view>
		<button @click="requestLogin">请求数据</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		onLoad(){
		},
		methods: {
			async requestLogin(){
				// console.log(11111111)
				// const data = {
				// 	email:'test@a.com',
				// 	password:'123123'
				// }
				// const res = await this.$u.api.authLogin(data)
				// console.log(res)
				// console.log(22222222)
				
				console.log(this.vuex_version)
				this.$u.vuex('vuex_name','Tom');
				console.log(this.vuex_name)
				
				
			}
			
		}
	}
</script>

<style>

</style>
