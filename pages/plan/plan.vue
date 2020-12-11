<template>
	<view>
		<!-- 顶部   需要数据 planname-->
		<view class="header">已生成<text class="plan-text" space="ensp">  脑卒中康复  </text>计划 <view class="change-btn">修改计划</view></view>
		<!-- 数据栏 -->
		<view class="big-data-box">
			<view class="data-box">
				<text class="dt-title">训练周期</text>
				<view class="dt"><text>14</text>天</view>
			</view>
			<view class="data-box">
				<text class="dt-title">每周训练</text>
				<view class="dt"><text>4~5</text>天</view>
			</view>
			<view class="data-box">
				<text class="dt-title">每日时长</text>
				<view class="dt"><text>30~50</text>分钟</view>
			</view>
		</view>
		<!-- <image src="../../static/inquiry-active.png" mode="aspectFit" class="course-logo"></image> -->
		<!-- 日历    导入的组件    https://ext.dcloud.net.cn/plugin?id=1732 -->
		<!-- 需要数据 dotlist（需要被标记的日期） -->
		<view class="calendar">
			<view class="calendar-title">日程信息</view>
			<zzx-calendar @selected-change="datechange" showBack="true"></zzx-calendar>
		</view>
		<!-- 今日项目栏 -->
		<!-- 通过isToday判断是否显示-->
		<!-- 需要数据 courses   course.date   course.logo   course.name   course.now   course.num-->
		<view class="items">今日项目</view>
		<!-- <view class="items-list">
			<view class="course-card" v-for="(course,index) in userPlanTable.planTable[0]" :key="index" @tap="courseStart" :data-courseid=course.id>
				<image :src="course.logo" mode="aspectFit" class="course-logo"></image>
				<view class="today-course-name">{{course.name}}</view>
				<view class="today-course-action">开始课程</view>
			</view>
		</view> -->
		<view class="items-list">
			<view class="course-card" @tap="courseStart">
				<image src="../../static/背部放松.jpg" mode="aspectFit" class="course-logo" ></image>
				<view class="today-course-name">背部（背阔肌）放松训练</view>
				<view class="today-course-action">开始课程</view>
			</view>
			<view class="course-card" @tap="courseStart">
				<image src="../../static/肩关节放松.jpeg" mode="aspectFit" class="course-logo" ></image>
				<view class="today-course-name">肩关节放松训练</view>
				<view class="today-course-action">开始课程</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userPlanTable:{}
				
			}
		},
		// onLoad:function(){
		// 	this.getPlanTable()
		// },
		 methods: {
			courseStart(e) {
				/* var courseId = e.currentTarget.dataset.courseid */
			uni.navigateTo({
				/* url:'../course/course?courseId='+courseId */
				url:'../course/course'
				
		 		})
		 	},
		// 	getPlanTable(){
		// 		uni.request({
		// 			url: 'http://47.96.117.8:3000/get_user_plan/4',
		// 			method: 'GET',
		// 			data:{},
		// 			success: res => {
		// 				this.userPlanTable=res.data.data
		// 				console.log(this);
		// 			},
		// 			fail: () => {},
		// 			complete: () => {}
		// 		});
		// 	},
		// 	getPlanId(){
		// 	}
		 }
	}
	
</script>

<style>
	view{
		font-size: 25rpx;
	}
	.header{
		padding: 10rpx;
		font-size: 35rpx;
	}
	.header text{
		color: #4CD964;
	}
	.calendar-title{
		font-size: 35rpx;
	}
	.change-btn{
		display: inline-block;
		border: 3rpx solid #00aaff;
		font-size: 30rpx;
		padding: 2rpx;
		border-radius: 5rpx;
		position: relative;
		left: 250rpx;
	}
	.big-data-box{
		display: flex;
		justify-content: space-evenly;
		border-bottom: 1rpx solid #c8c7cc;
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
	}
	.dt{
		position: relative;
		top: 25rpx;
	}
	.dt text{
		color: #ff00ff;
		font-size: 40rpx;
	}
	.calendar-title{
		position: relative;
		left: 10rpx;
	}
	.course-logo{
		width: 150rpx;
		height: 150rpx;
		position: relative;
		top:10rpx;
		left: 10rpx;
	}
	.choices{
		display: flex;
		flex-direction: row;
	}
	.choose-action{
		width: 211rpx;
		height: 50rpx;
		padding: 20rpx;
		text-align: center;
		border: 5rpx solid #00aaff;
	}
	.items-list{
		border-bottom: 2rpx solid #c8c7cc;
		border-top: 2rpx solid #c8c7cc;
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 20rpx;
	}
	.items{
		padding: 20rpx;
		padding-left: 10rpx;
		padding-top: 40rpx;
		font-size: 35rpx;
	}
	.course-card{
		width: 650rpx;
		height: 180rpx;
		border: 4rpx solid #c8c7cc;
		border-bottom: 1rpx solid #c8c7cc;
		border-top: 1rpx solid #c8c7cc;
		
	}
	.today-course-name{
		position: relative;
		left: 190rpx;
		bottom: 140rpx;
		font-size: 30rpx;
	}
	.today-course-progress{
		position: relative;
		left: 190rpx;
		bottom: 130rpx;
	}
	.today-course-action{
		position: relative;
		left: 500rpx;
		bottom: 80rpx;
		font-size: 30rpx;
	}
	.calendar{
		padding-top: 30rpx;
	}
	
</style>
