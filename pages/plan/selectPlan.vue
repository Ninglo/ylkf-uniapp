<template>
	<view>
		<view class="header">
			<text>根据您的选择，</text>
			<text>我们为您找到以下备选方案：</text>
		</view>
		<form @submit="" @reset="">
			<view class="plan-box">
				<swiper indicator-dots="true">
					<swiper-item class="">
						<view class="content-box">
							<text class="conten-title">方案一</text>
							<text>该方案有以下课程：XXXX，yyyy,oooo.</text>
							<text>持续时间：10~20天</text>
							<text>难度：难</text>
							<text>预期效果：可以ooooo，llll</text>
							<text>适合人群：患者</text>
						</view>
					</swiper-item>
					<swiper-item class="">
						<view class="content-box">
							<text class="conten-title">方案二</text>
							<text>该方案有以下课程：XXXX，yyyy,oooo.</text>
							<text>持续时间：10~20天</text>
							<text>难度：难</text>
							<text>预期效果：可以ooooo，llll</text>
							<text>适合人群：患者</text>
						</view>
					</swiper-item>
					<swiper-item class="">
						<view class="content-box">
							<text class="conten-title">方案三</text>
							<text>该方案有以下课程：XXXX，yyyy,oooo.</text>
							<text>持续时间：10~20天</text>
							<text>难度：难</text>
							<text>预期效果：可以ooooo，llll</text>
							<text>适合人群：患者</text>
						</view>
					</swiper-item>
				</swiper>
			</view>
			<button form-type="submit" @click="choose">选定方案</button>
		</form>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			choose(){
				uni.showModal({
					showCancel:true,
					title:"确认选择该方案？",
					content:"若已有方案，则直接替换现有方案，该操作不可撤销）",
					cancelText:"再想想",
					success(res) {
						if (res.confirm){
							console.log('确认')
							uni.switchTab({
								url:"plan",
								fail(e){
									console.log(e)
								}
							})
						}
					}
				})
			}
		}
	}
</script>

<style>
	text{
		display: block;
		padding: 5rpx;
	}
	.header{
		padding: 10rpx;
	}
	.header text{
		color: #00AAFF;
		size: 40rpx;
		margin-bottom: 20rpx;
	}
	swiper{
		height: 700rpx;
		border: #999999 solid 1rpx;
		margin: 10rpx;
	}
	.content-box{
		width: 80%;
		height: 80%;
		position: relative;
		left: 10%;
		top: 10%;
	}
	.conten-title{
		text-align: center;
		
	}
	button{
		background: none;
		width: 50%;
		margin-top: 100rpx;
		
	}
</style>
