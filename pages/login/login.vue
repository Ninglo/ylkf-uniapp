<template>
	<view class="main">
		<view class="">
		<image src="../../static/logo.png" mode="aspectFit"></image>
		</view>
		<button type="primary"  @tap="gotoPlan" >微信一键登录</button>
		<navigator url="" class="nav">其他方式登录></navigator>
		<checkbox-group  >
			<label style="display: flex;flex-direction: row;font-size: 30rpx;">
				<checkbox value="yes"/><span style="display: flex;flex-direction: row;">我已经阅读并接受<navigator url="../xieyi/xianyi" open-type="navigate" style="color: #FF6000;">用户服务协议</navigator>、<navigator url="../xieyi/xianyi" open-type="navigate" style="color: #FF6000;">隐私政策</navigator></span>
			</label>
		</checkbox-group>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			gotoPlan: function() {
				
				uni.switchTab({
					url:'../plan/plan_old'
				})
			},
		}
	}
</script>

<style>
	
.main{
	text-align: center;
}
img{
	width: 150rpx;
	height: 100rpx;
}
button{
	position: relative;
	top: 200rpx;
	width: 80%;
}
.nav{
	position: relative;
	top: 220rpx;
}

checkbox-group {
	position: relative;
	top: 300rpx;
	left: 80rpx;
	width: 90%;
}
checkbox-group span{
	position: relative;
	top: 10rpx;
}
</style>
