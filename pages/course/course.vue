<template>
	<view>
		<!-- 上部分的课程名称与开始课程键 -->
		<!-- 通过courseStart方法跳转到对应视频页 -->
		<!-- 需要数据 course.name -->
		<view class="course-box">
			<text class="course-name">{{course.name}}</text>
			<view class="course-start" @tap="courseStart">开始课程</view>
		</view>
		<!-- 一些课程信息 -->
		<!-- 需要数据 course.info -->
		<view class="course-info">
			<text>    {{course.info}}
			</text>
		</view>
		<!-- 动作列表页-->
		<!-- 遍历course里的actions数组 -->
		<!-- 需要数据 course.actions -->
		<!-- action.name   action.logo   action.point   action.learnmore -->
		<view class="action-list">
			<view class="action-card" v-for="(action,index)" in course.actions>
				<image :src="action.logo" mode="aspectFit" class="action-logo"></image>
				<view class="action-name">动作{{index+1}}    {{action.name}}</view>
				<view class="action-point">{{action.point}}</view>
				<navigator url="action.learnmore" class="action-learnmore">详情了解</navigator>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				course: {}
			}
		},
		onLoad:function(e){
			console.log(e)
			uni.request({
				url: 'http://47.96.117.8:3000/get_course_plan/'+e.courseId,
				method: 'GET',
				data:{},
				success: res => {
					console.log(res)
					this.course=res.data.data
				},
				fail: () => {},
				complete: () => {}
			})
		},
		methods: {
			
		}
	}
</script>

<style>
	.course-box{
		border-top: 4rpx solid #c8c7cc;
		border-bottom: 4rpx solid #c8c7cc;
		width: 750rpx;
		height: 250rpx;	
		text-align: center;
		padding:30rpx ;
	}
	.course-info{
		padding: 20rpx;
		margin-top: 20rpx;
		margin-bottom: 20rpx;
		border-top: 4rpx solid #c8c7cc;
		border-bottom: 4rpx solid #c8c7cc;
		text-align: center;
	}
	.course-name{
		padding-top: 20rpx;
		font-size: 50rpx;
	}
	.course-start{
		position: relative;
		border: 4rpx solid #c8c7cc;
		width: 300rpx;
		top: 100rpx;
		left:200rpx;
		padding: 10rpx;
	}
	.action-list{
		border: 5rpx solid #c8c7cc;
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 20rpx;
	}
	.action-card{
		width: 650rpx;
		height: 180rpx;
		border: 4rpx solid #c8c7cc;
		border-bottom: 2rpx solid #c8c7cc;
		border-top: 2rpx solid #c8c7cc;
	}
	.action-logo{
		width: 150rpx;
		height: 150rpx;
		position: relative;
		top:10rpx;
		left: 10rpx;
	}
	.action-name{
		position: relative;
		left: 180rpx;
		bottom: 150rpx;
	}
	.action-point{
		position: relative;
		left: 180rpx;
		bottom:145rpx;
		font-size: 20rpx;
	}
	.action-learnmore{
		position: relative;
		left: 500rpx;
		bottom: 100rpx;
	}
</style>
