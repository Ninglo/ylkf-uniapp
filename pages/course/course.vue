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
			<view class="action-card" v-for="(action,index) in course.actions>
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
		border-top: 4upx solid #c8c7cc;
		border-bottom: 4upx solid #c8c7cc;
		width: 750upx;
		height: 250upx;	
		text-align: center;
		padding:30upx ;
	}
	.course-info{
		padding: 20upx;
		margin-top: 20upx;
		margin-bottom: 20upx;
		border-top: 4upx solid #c8c7cc;
		border-bottom: 4upx solid #c8c7cc;
		text-align: center;
	}
	.course-name{
		padding-top: 20upx;
		font-size: 50upx;
	}
	.course-start{
		position: relative;
		border: 4upx solid #c8c7cc;
		width: 300upx;
		top: 100upx;
		left:200upx;
		padding: 10upx;
	}
	.action-list{
		border: 5upx solid #c8c7cc;
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 20upx;
	}
	.action-card{
		width: 650upx;
		height: 180upx;
		border: 4upx solid #c8c7cc;
		border-bottom: 2upx solid #c8c7cc;
		border-top: 2upx solid #c8c7cc;
	}
	.action-logo{
		width: 150upx;
		height: 150upx;
		position: relative;
		top:10upx;
		left: 10upx;
	}
	.action-name{
		position: relative;
		left: 180upx;
		bottom: 150upx;
	}
	.action-point{
		position: relative;
		left: 180upx;
		bottom:145upx;
		font-size: 20upx;
	}
	.action-learnmore{
		position: relative;
		left: 500upx;
		bottom: 100upx;
	}
</style>
