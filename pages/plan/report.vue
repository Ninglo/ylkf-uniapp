<template>
	<view>
		<!-- 数据栏 -->
		<view class="big-data-box">
			<view class="data-box">
				<text class="dt-title">锻炼天数</text>
				<view class="dt"><text>14</text>天</view>
			</view>
			<view class="data-box">
				<text class="dt-title">累计锻炼</text>
				<view class="dt"><text>1000</text>分钟</view>
			</view>
			<view class="data-box">
				<text class="dt-title">完成度</text>
				<view class="dt"><text>30</text>%</view>
			</view>
		</view>
		<view class="middle">
			<text>锻炼情况</text>
			<view class="data-view"> </view>
		</view>
		<view class="foot">
			<text>还记得吗...？</text>
			<view class="record-box">
				<view class="choose-time">
					<image src="../../static/llast.png" mode="aspectFit"></image>
					<image class="ll" src="../../static/last.png" mode="aspectFit"></image>
					<view class="time">11月20日</view>
					<image class="ll" src="../../static/later.png" mode="aspectFit"></image>
					<image src="../../static/llater.png" mode="aspectFit"></image>
				</view>
				
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
								<view class="course-list" v-for="item in course">
												<image style="width: 50rpx; height: 50rpx;" src="../../static/finish.png"></image>
												<view class="finish">完成{{item.name}}课程</view>
											</view>
							</view>
					
				
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
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
	.big-data-box{
		display: flex;
		justify-content: space-evenly;
		border-bottom: #C0C0C0 solid 1rpx;
		margin: 20rpx;
		padding-bottom: 20rpx;
		
	}
	.data-box{
		width: 200rpx;
		height: 125rpx;
		text-align: center;
		display: inline-block;
	}
	.dt-title{
		position: relative;
		top: 20rpx;
		font-size: 25rpx;
	}
	.dt{
		position: relative;
		top: 30rpx;
		font-size: 25rpx;
	}
	.dt text{
		color: #ff00ff;
		font-size: 40rpx;
	}
	.middle text{
		padding: 10rpx;
	}
	.data-view{
		background-color: #C0C0C0;
		height: 400rpx;
	}
	
	.choose-time{
		background-color:#d1d3ce ;
		text-align: center;
	}
	.choose-time image{
		width: 60rpx;
		height: 60rpx;
		margin-left: 20rpx;
	}
	.choose-time .ll{
		width: 40rpx;
	}
	.foot{
		
		padding: 20rpx;
		position: relative;
		top: 10rpx;
		border: #C0C0C0 solid 1rpx;
	}
	.foot text{
		text-align: left;
	}
	.time{
		display: inline-block;
		position: relative;
		bottom: 14rpx;
		margin-left: 60rpx;
		margin-right: 60rpx;
	}
	.record-box{
		width: 90%;
		border: #C0C0C0 solid 1rpx;
		position: relative;
		left: 5%;
		margin: 10rpx;
	}
		.content {
			width: 100%;
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
