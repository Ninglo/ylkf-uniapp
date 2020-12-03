<template>
	<view>
		<view class="title">第 7 天</view>
		<view class="title">恭喜你，已完成今日全部锻炼计划</view>
		<view class="content">
			<view class="user-img"><open-data type="userAvatarUrl"></open-data></view>
			<view class="user-name"><open-data type="userNickName"></open-data></view>
			<text class="date">{{ date }}</text>
			<view class="divide-line"></view>
			<view class="course-num-time">
				<text space="emsp">课程      用时</text>
			</view>
			<view class="course-num-time">
				<text class="course-num">{{courseNum}}</text>
				<text class="course-time" space="emsp">节   {{courseTime}}</text>
			</view>
		</view>
		<view class="content">
			<view style="margin: 5% 10%;">本次锻炼的感受是？</view>
			<view class="out-box">
				<view class="feeling-box">太简单了</view>
				<view class="feeling-box">还不错</view>
				<view class="feeling-box">太难了</view>
			</view>
			<view style="text-align: center; font-size: 30rpx; margin: 40rpx 20rpx; color: #999999;">
				你的反馈将帮助我们为你推荐更合适的锻炼计划
			</view>
		</view>
		<view class="content">
			<view class="course-list" v-for="item in course">
				<image style="width: 50rpx; height: 50rpx;" src="../../static/finish.png"></image>
				<view class="finish">完成{{item.name}}课程</view>
			</view>
		</view>		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				date: new Date().toLocaleDateString(),
				courseNum: 3,
				courseTime: "03:27:39",
				course: [
					{
						name: "课程1"
					},
					{
						name: "课程2"
					}
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	.title {
		margin: 20rpx;
		font-size: 40rpx;
		font-weight: bold;
	}
	
	.content {
		margin: 40rpx 20rpx 20rpx;
		width: 700rpx;
		border: 1rpx #808080 solid;
		border-radius: 10rpx;
	}
	
	.user-img {
		margin: 5% 10%;
		width: 150rpx;
		height: 150rpx;
		display: inline-block;
		border-radius: 50%;
	}

	.user-name {
		display: inline-block;
		position: relative;
		bottom: 100rpx;
	}
	
	.date {
		position: relative;
		right: 70rpx;
	}
	
	.divide-line {
		background: #E0E3DA;
		width: 80%;
		height: 5rpx;
		position: relative;
		left: 10%;
		top: 10rpx;
	}
	
	.course-num-time {
		margin: 20rpx 10%;
	}
	
	.course-num, .course-time {
		color: purple;
		font-weight: bold;
		font-size: 50rpx;
	}
	
	.out-box {
		display: flex;
		justify-content: center;
	}
	
	.feeling-box {
		margin-left: 7.5%;
		margin-right: 7.5%;
		width: 120rpx;
		height: 120rpx;
		background-color: #C0C0C0;
		border: 1rpx #808080 solid;
		border-radius: 10rpx;
		display: inline-flex;
		align-items: center;
		justify-content: center;
	}
	
	.course-list {
		margin: 15rpx 30rpx 10rpx 30rpx;
		height: 60rpx;
	}
	
	.finish {
		margin-left: 80rpx;
		position: relative;
		bottom: 60rpx;
	}
</style>
