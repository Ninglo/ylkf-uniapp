<template>
	<view>
		<!-- 视频 course.action.video -->
		<view class="video-box">
			<video src="course.action.video" controls></video>
		</view>
		<!-- 动作具体详情  course.action.info-->
		<view class="action-info">
			<text>    {{course.action.info}}</text>
		</view>
		<view class="action-choose">
			<view class="action-box">前一个动作</view>
			<view class="action-box">目前动作</view>
			<view class="action-box">下一个动作</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				course: []
			}
		},
		methods: {
			onLoad:function(){
					uni.request({
						url: '',
						method: 'GET',
						data: {
							course: []
						},
						success: res => {
							this.course=res.data;
						},
						fail: () => {},
						complete: () => {}
					});
			}
		}
	}
</script>

<style>
	.action-choose{
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		border: 4rpx solid #c8c7cc;
	}
	.action-box{
		padding: 10rpx;
		border: 2rpx solid #c8c7cc;
		border-left: 4rpx solid #c8c7cc;
		border-right: 4rpx solid #c8c7cc;
	}
	.action-info{
		padding: 20rpx;
		margin-top: 20rpx;
		margin-bottom: 20rpx;
		border-top: 4rpx solid #c8c7cc;
		border-bottom: 4rpx solid #c8c7cc;
		text-align: center;
	}
	.video-box{
		display: flex;
		flex-direction: column;
		align-items: center;
		width: 750rpx;
		padding-top: 20rpx;
		padding-bottom: 20rpx;
		border-top: 4rpx solid #c8c7cc;
		border-bottom: 4rpx solid #c8c7cc;
	}
</style>
