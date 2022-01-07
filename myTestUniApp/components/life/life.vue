<template>
</template>

<script>
	export default{
		name:'life',
		data(){
			return{
				
			};
		},
		//在实例初始化之后，数据观测(data observer) 和 event/watcher事件配置之前被调用
		beforeCreate() {
			console.log('beforeCreate')
		},
		//在实例创建完成后被立即调用。在这一步，实例已完成以下的配置：数据观测 (data observer)，属性和方法的运算，watch/event 事件回调。然而，挂载阶段还没开始，$el 属性目前不可见。
		created(){
			console.log('created')
		},
		//el 被新创建的 vm.$el 替换，并挂载到实例上去之后调用该钩子。如果 root 实例挂载了一个文档内元素，当 mounted 被调用时 vm.$el 也在文档内。 
		mounted() {
			console.log('mounted')
		},
		//Vue 实例销毁后调用。调用后，Vue 实例指示的所有东西都会解绑定，所有的事件监听器会被移除，所有的子实例也会被销毁。 
		destroyed() {
			
		}
		
	}
</script>

<style>
</style>
