<template>
	<view class="message-box">
		<view class="message_content">
		<scroll-view class="message_scroll" scroll-y="true" >
			<block v-for="(item,index) in chatList" :key="index">
				<view class="me_message-cell" v-if="!item.isMe">
					<image class="me-head-icon" src="@/static/header_me.png"></image>
					<view class="me-message-info">
						<text class="me_message_title">张三</text>
						<text class="me_message-content" v-if="item.type === 'text'">{{item.content}}</text>
						<image class="me_message-content-img" v-if="item.type ==='image'" :src="item.content" mode="widthFix"></image>
					</view>
				</view>
				<view class="friend_message-cell" v-if="item.isMe">
					<view class="friend-message-info">
						<text class="friend_message_title">小六</text>
						<text class="friend_message-content" v-if="item.type === 'text' ">{{item.content}}</text>
						<image class="friend_message-content-img" v-if="item.type ==='image'" :src="item.content" mode="widthFix"></image>
					</view>
					<image class="friend-head-icon" src="@/static/header_friend.png"></image>
				</view>
			</block>
		</scroll-view>
		</view>
		<view class="chat-footer">
			<input class="msg-input" type="text" cursor-spacing="16" v-model="messagestr">
			<image class="img-chose" src="../../static/tab_icon_创作@2x.png"@click="choseImgAndSend"></image>
			<view class="send-btn" @click="sendMsg">发送</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				chatList:[{
					isMe:false,
					type:'text',
					content:'你好呀！你想说什么呢？'
				},{
					isMe:false,
					type:'image',
					content:'../../static/message-image.png'
				},{
					isMe:true,
					type:'text',
					content:'哇，你真漂亮呀'
				},{
					isMe:true,
					type:'image',
					content:'../../static/f-message-image.png'
				},{
					isMe:false,
					type:'text',
					content:'你好呀！你想说什么呢？'
				}],
				messagestr:''
			}
		},
		methods: {
			toMe(){
				uni.navigateTo({
					url:'../me/me'
				})
			},
			onShow(){
				if(!!uni.getStorageInfoSync('chatList')){
					this.chatList = JSON.parse(uni.getStorageInfoSync('chatList'))
					uni.pageScrollTo({
						scrollTop:99999999,
						duration:0
					})
				}
			},
			choseImgAndSend(){
				uni.chooseImage({
					count:1,
					sizeType:['original','compressed'],
					sourceType:['album','camera'],
					success: res => {
						let senMsg ={
							isMe:true,
							type:'image',
							content:res.tempFilePaths[0]
						}
						this.chatList.push(senMsg);
						
						let meSenMsg ={
							isMe:false,
							type:'image',
							content:res.tempFilePaths[0]
						}
						this.chatList.push(meSenMsg);
						uni.pageScrollTo({
							scrollTop:99999999,
							duration:0
						})
						uni.setStorageSync('chatList',JSON.stringify(this.chatList))
					}
				})
			},
			sendMsg(){
				let senMsg ={
					isMe:true,
					type:'text',
					content:this.messagestr
				}
				this.chatList.push(senMsg);
				
				let meSenMsg ={
					isMe:false,
					type:'text',
					content:this.messagestr
				}
				this.chatList.push(meSenMsg);
				uni.pageScrollTo({
					scrollTop:99999999,
					duration:0
				})
				
			}
			
		},
	}
</script>

<style>
	.message-box{
		display: flex;
		flex-direction: column;
	}
	.me_message-cell{
		display: flex;
		flex-direction: row;
		margin: 10px 10px 10px 10px;
		background-color: #C0C0C0;
		
	}
	.me-head-icon{
		width: 44px;
		height: 44px;
		margin: 10px 10px 10px 10px;
	}
	.me-message-info{
		display: flex;
		flex-direction: column;
		flex:1;
		overflow:hidden;
		word-wrap:break-word;
		word-break:break-all;
		font-size:12px;
	}
	.me_message_title{
		color: #333333;
		font-size: 14px;
		margin: 10px 10px 10px;
	}
	.me_message-content{
		color:#DD524D;
		font-size: 18px;
		margin:0px 10px 10px 10px;
		background-color: #FFFFFF;
		border-style:solid;
		border-width:1px;
	}
	.friend_message-cell{
		display: flex;
		flex-direction: row;
		margin: 10px 10px 10px 10px;
		background-color:#F0AD4E;
	}
	.friend-head-icon{
		width: 44px;
		height: 44px;
		margin: 10px 10px 10px 10px;
	}
	.friend-message-info{
		display: flex;
		flex-direction: column;
		flex:1;
		overflow:hidden;
		word-wrap:break-word;
		word-break:break-all;
		font-size:12px;
		text-align:right;
	}
	.friend_message_title{
		color: #333333;
		font-size: 14px;
		margin: 10px 10px 10px;
		text-align:right;
	}
	.message_scroll {
	  /* position: fixed; */
	  bottom: 64px;
	 /* max-height: calc(100%) !important;
	  height: calc(100%) !important; */
	  /* margin-top: 164px; */
	  /* overflow-y: hidden !important; */
	}
	.message-cell {
		/* overflow-y: hidden !important; */
	}
	.chat-footer{
		display: flex;
		flex-direction: row;
		/* top: calc(100% - 64px); */
		bottom: 0px;
		background-color: #C0C0C0;
		width: 100%;
		height: 64px;
		align-items: center;
	}
	.msg-input{
		margin: 10px;
		background-color: #FFFFFF;
		flex: 1;
	}
	.img-chose{
		margin: 0px 10px 0px 0px;
		width: 40px;
		height: 40px;
	}
	.send-btn{
		margin: 10px 10px 10px 0px;
		width: 60px;
		height: 40px;
		background-color: #4CD964;
		color: #FFFFFF;
		border-radius: 8px;
		border-style:solid;
		border-width:1px;
		border-color: #4CD964;
		text-align: center;
	}
	
</style>
