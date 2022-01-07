<script>
	export default {
		/**
		 应用的生命周期
		 
		 页面的生命周期
		 
		 组件的生命周期
		 */
		//应用初始化完成执行，全局只执行一次
		onLaunch: function() {//当uni-app初始化完成触发（全局只触发一次）
		//登录的处理 全局变量....
			console.log('App Launch')
		},
		//应用显示的时候执行，或者从后台进入前台
		onShow: function() {//当uni-app启动，或从后台进入前台显示
			console.log('App Show')
		},
		//应用隐藏的时候执行，或者从前台进入后台
		onHide: function() {//当uni-app 从前台进入后台
			console.log('App Hide')
		},
		onPageNotFound() {
			uni.navigateTo({
				url:'pages/404/404/404'
			})
			
		}
	}
</script>

<style lang="scss">
	
	/* 注意要写在第一行，同时给style标签加入lang="scss"属性 */
	@import "uview-ui/index.scss";
	
</style>
