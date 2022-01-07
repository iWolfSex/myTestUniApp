<template>
	<view>
		<child :msg="title" @childEvent="sayHello"></child>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title:'Hello',
			}
		},
		components:{
		},
		methods: {
			sayHello(msg){
				this.title = msg
			}
			
		}
	}
</script>

<style>
	*{
		color:#4CD964;
	}

</style>
