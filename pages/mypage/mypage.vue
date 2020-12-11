<template>
	<view>
		<image src="../../static/背景.jpg" mode="aspectFill" class="bg-image"></image>
		<button v-show="loginButtonShow" open-type="getUserInfo" @getuserinfo="bindgetuserinfo" withCredentials="true">登录</button>
		<view v-if="userInfoShow">
			<image class="user-img" :src="avatarUrl"></image>
			<text class="user-name">{{ nickName }}</text>
			<navigator class="setting-nav">
				<image class="setting-img" src="../../static/setting.png"></image>
			</navigator>		
			<view @click="onOpenPromptClick()" class="user-info-change">
				<image class="change-user-info" src="../../static/change-user-info.png"></image>
				<view class="user-info">{{ userInfo }}</view>
			</view>
			<yomol-prompt :title="promptTitle" :inputType="promptInputType" :maxlength="maxlength" :defaultValue="promptDefaultValue" :func="promptFunc" ref="yomolPrompt" @onConfirm="onPromptConfirm"></yomol-prompt>
			
			<view @click="getBodyData()" class="data-button"><text>身体数据</text></view>
			<view @click="getCourseData()" class="data-button"><text>课程报告</text></view>
			<view class="body-data" v-if="bodyDataShow">
				<view class="data-list">身高：180cm</view>
				<view class="data-list">体重：55kg</view>
				<view class="data-list">年龄：44</view>
				<view class="data-list">健康状态：亚健康</view>
			</view>
			<view class="course-data" v-if="courseDataShow">
				<navigator url="../plan/report" class="course" v-for="item in courses">
					{{item.name}}课程（{{item.state}})
					<view  class="course-nav">
						>
					</view>
				</navigator>
			</view>
		</view>
	</view>
</template>

<script>
	import yomolPrompt from '@/components/yomol-prompt/yomol-prompt.vue';
	export default {
		components:{
			yomolPrompt
		},
		data() {
			return {
				avatarUrl: "",
				nickName: "",
				loginButtonShow: true,
				userInfoShow: false,
				userInfo: "something about me.",
				
				promptTitle: '提示',
				promptDefaultValue: '',
				promptInputType: 'text',
				promptFunc: "", //空值不执行
				maxlength: 30,
				
				bodyDataShow: true,
				courseDataShow: false,
				courses: [
					{
						name: "拉伸训练",
						state: "进行中"
					},
					{
						name: "感知恢复",
						state: "已完成"
					}
				]
			}
		},
		methods: {
			bindgetuserinfo: function(res) {
				this.avatarUrl = res.detail.userInfo.avatarUrl
				this.nickName = res.detail.userInfo.nickName
				this.loginButtonShow = false
				this.userInfoShow = true
			},
			/* 
			* 打开提示框
			*/
			onOpenPromptClick: function() {
				this.promptTitle = '修改个人简介' //提示名称
				this.promptDefaultValue = this.userInfo //默认值
				this.promptInputType = 'text' //输入类型 同Input组件
				this.maxlength = 30 //最大长度
				this.promptFunc = "update-prompt" //将定义好的处理逻辑名传给组件回调
				this.$refs.yomolPrompt.show()
			},
			/* 
			* 输入内容
			*/
			onPromptConfirm: function(e){
				console.log(e);
			},
			getBodyData: function() {
				this.bodyDataShow = true,
				this.courseDataShow = false
			},
			getCourseData: function() {
				this.bodyDataShow = false,
				this.courseDataShow = true
			}
		},
		onBackPress() {
			if(this.$refs.yomolPrompt.visible){
				this.$refs.yomolPrompt.hide()
				return true
			}
		},
		onLoad(e) {
			//自定义input处理事件监听
			uni.$on('update-prompt',(data)=>{
				// data.value input输入值
				// data.callback 处理后返回方法名
				let val = data.value
				//逻辑处理

				uni.$emit(e.callback,val)
			})
		},
		onUnload() {
			/* 移除事件监听 */
			uni.$off('update-prompt')
		},
	}
</script>

<style>
	.bg-image{
		z-index: -1;
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}
	.user-img {
		height: 200rpx;
		width: 200rpx;
		border-radius: 50%;
		margin: 20rpx;
	}
	
	.user-name {
		position: relative;
		bottom: 150rpx;
		left: 20rpx;
		font-size: 35rpx;
	}
	
	.user-info-change {
		position: relative;
		bottom: 125rpx;
		left: 245rpx;
	}
	
	.user-info {
		display: inline;
		font-size: 30rpx;
		width: 400rpx;
	}
	
	.change-user-info {
		width: 70rpx;
		height: 70rpx;
		margin-right: 10rpx;
		position: relative;
		top: 15rpx;
	}
	
	.setting-nav {
		position: relative;
		bottom: 150rpx;
		left: 350rpx;
		display: inline;
	}
	
	.setting-img {
		width: 70rpx;
		height: 70rpx;
	}
	.data-list{
		padding: 5rpx;
		}
	.data-button {
		margin: 0 25rpx;
		justify-content: center;
		width: 320rpx;
		height: 100rpx;
		border-radius: 25rpx;
		border: 1rpx #999999 solid;
		display: inline-flex;
		align-items: center;
		position: relative;
		bottom: 50rpx;
	}
	
	.body-data {
		margin: 30rpx;
	}
	
	.course {
		margin: 10rpx 20rpx;
		padding: 15rpx;
		width: 675rpx;
		height: 150rpx;
		background-color: #9fefef;
		border-radius: 10rpx;
		display: flex;
		align-items: center;
		justify-content: left;
		color: #808080;
	}
	
	.course-nav {
		position: absolute;
		right: 40rpx;
		font-size: 50rpx;
	}
</style>
