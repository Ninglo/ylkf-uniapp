<template>
	<view>
		<view class="question">
			请选择疾病类型：
		</view>
		<view class="answer-box">
			<view class="answer" v-for="(item,index) in answerArr" :key="index" :class="{'active':isSelect==index}" @tap="choose(index)" >{{item.num}}.{{item.info}}</view>
		</view>
		<view class="">
			<button type="primary" @tap="gotoNext">确定</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				answerArr:[
					{num:'A',info:'脑卒中'},
					{num:'B',info:'帕金森'},
					{num:'C',info:'小儿麻痹后遗症'},
					{num:'D',info:'心肺康复'}],
				isSelect:'-1'
			}
		},
		methods: {
			//单选
			choose(e){
				console.log(e)
				if(e!=this.isSelect){
					this.isSelect = e
				}else{
					this.isSelect = '-1'
				}
				
			},
			gotoNext(e) {
				if (this.isSelect!='-1'){
					uni.navigateTo({
					url:'questionnaire'
					})
				}else{
					uni.showModal({
						content:'请选择疾病类型',
						showCancel:false
					})
				}
			},
		}
	}
</script>

<style>
	.green{
		background-color: green;
	}
	.question{
		width: 80%;
		margin: 15rpx;
		padding-top: 40rpx;
		padding-bottom: 40rpx;
		border:1rpx solid #c8c7cc ;
		border-radius: 5rpx;
		text-align: center;
		font-size: 48rpx;
		position: relative;
		left: 10%;
	}
	.answer-box{
		width: 80%;
		margin-top: 10%;
		position: relative;
		left: 10%;
	}
	.answer{
		width: 100%;
		padding: 5rpx;
		padding-top: 20rpx;
		padding-bottom: 20rpx;
		border:1rpx solid #c8c7cc ;
		border-radius: 5rpx;
		margin: 10rpx;
	}
	button{
		width: 60%;
		position: absolute;
		bottom: 10%;
		left: 20%;
	}
	.active{
		background-color: #00AAFF;
		color: #F8F8F8;
	}
</style>
