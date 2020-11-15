<template>
	<view>
		<!-- 顶部    还未实现跳转 -->
		<view class="choices">
			<view class="choose-action">添加计划</view>
			<view class="choose-action">计划表</view>
			<view class="choose-action">课程库</view>
		</view>
		<!-- 日历    导入的组件    https://ext.dcloud.net.cn/plugin?id=1732 -->
		<!-- 需要数据 dotlist（需要被标记的日期） -->
		<view class="calendar">
			<zzx-calendar @selected-change="datechange" showBack="true"></zzx-calendar>
		</view>
		<!-- 今日项目栏 -->
		<!-- 通过isToday判断是否显示-->
		<!-- 需要数据 courses   course.date   course.logo   course.name   course.now   course.num-->
		<view class="items">今日项目</view>
		<view class="items-list">
			<view class="course-card" v-for="(course,index) in userplanTable.planTable[0]" :key="index" >
				<image src="course.logo" mode="aspectFit" class="course-logo"></image>
				<view class="today-course-name">{{course.name}}</view>
				<!-- <view class="today-course-progress">{{course.now}}/{{course.num}}</view> -->
				<view class="today-course-action" @tap="courseStart">开始课程</view>
			</view>
		</view>
		<!-- 所有已添加的课程，不需要用v-if进行判断 -->
		<!-- 需要数据 courses   course.logo   course.name -->
		<!-- <view class="items">正在进行的课程</view>
		<view class="items-list" >
			<view class="course-card" v-for="(course,index) in courses" :key="index">
				<image src="course.logo" mode="aspectFit" class="course-logo"></image>
				<view class="course-name">{{course.name}}</view>
				<view class="course-action">查看详情</view>
			</view>
		</view> -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
			}
		},
		onLoad:function(){
			this.getPlanTable()
			
		},
		methods: {
			courseStart() {
				uni.navigateTo({
					url: '../course/course'
				})
			},
			getPlanTable(){
				uni.request({
				url: 'http://192.168.43.214:3000/get_user_plan/4',
				method: 'GET',
				data: {
					userPlanTable:{
						id:"",
						date:"",
						name:"",
						planTable:[]
					}
				},
				success: res => {
					console.log(res.data);
					this.userplanTable.id = res.data.id,
					this.userplanTable.date = res.data.date,
					this.userplanTable.planTable = res.data.planTable
				},
				fail: () => {},
				complete: () => {}
			});
			},
			getPlanId(){
				
			}
		}
	}
	
</script>

<style>
	view{
		font-size: 35rpx;
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
		border: 5rpx solid #c8c7cc;
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 20rpx;
	}
	.items{
		padding: 20rpx;
		padding-left: 30rpx;
		padding-top: 40rpx;
	}
	.course-card{
		width: 650rpx;
		height: 180rpx;
		border: 4rpx solid #c8c7cc;
		border-bottom: 2rpx solid #c8c7cc;
		border-top: 2rpx solid #c8c7cc;
	}
	.today-course-name{
		position: relative;
		left: 190rpx;
		bottom: 140rpx;
	}
	.today-course-progress{
		position: relative;
		left: 190rpx;
		bottom: 130rpx;
	}
	.today-course-action{
		position: relative;
		left: 500rpx;
		bottom: 120rpx;
	}
/* 	.course-name{
		position: relative;
		left: 190rpx;
		bottom: 120rpx;
	}
	.course-action{
		position: relative;
		left: 500rpx;
		bottom: 80rpx;
	} */
	.calendar{
		padding-top: 30rpx;
	}
	
</style>
