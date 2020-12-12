<template>
	<view>
		<view class="QA" @tap="getIndex(index)" v-for="(item,index) in QA" :key="index">
			<view class="question">
				{{item.q}}
			</view>
			<view class="answer-box">
				<view class="answer" v-for="(answer,index) in item.a" :key="index" :class="{'active':item.isSelect==index}" @tap="choose(index,item.n)">{{answer.num}}.{{answer.info}}</view>
			</view>
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
				QA: [{
						q: '请问您患有什么疾病？',
						a: [{
								num: 'A',
								info: '脑卒中'
							},
							{
								num: 'B',
								info: '帕金森'
							},
							{
								num: 'C',
								info: '小儿麻痹后遗症'
							},
							{
								num: 'D',
								info: '心肺康复'
							}
						],
						isSelect: -1
					},
					{
						q: '距离您出院有多少天了？',
						a: [{
								num: 'A',
								info: '1周'
							},
							{
								num: 'B',
								info: '2周'
							},
							{
								num: 'C',
								info: '3周'
							},
							{
								num: 'D',
								info: '4周'
							}
						],
						isSelect: -1
					},
					{
						q: '您是否经历过康复训练？',
						a: [{
								num: 'A',
								info: '有过'
							},
							{
								num: 'B',
								info: '没有'
							}
						],
						isSelect: -1
					}
				],
				now: '-1'
			}
		},
		methods: {
			getIndex: function(index) {
				this.now = index
			},

			choose: function(e) {
				setImmediate(()=>{console.log(e)
				console.log(this.now)
				console.log(this.QA[this.now])
				if (e != this.QA[this.now].isSelect) {
					this.QA[this.now].isSelect = e
				} else {
					this.QA[this.now].isSelect = '-1'
				}})
				

			},
			gotoNext(e) {
				if (this.isSelect != '-1') {
					uni.navigateTo({
						url: 'selectPlan'
					})
				} else {
					uni.showModal({
						content: '请选择疾病类型',
						showCancel: false
					})
				}
			},
		}
	}
</script>

<style>
	.QA {
		margin: 10%;
	}

	.question {
		width: 100%;
		padding: 5rpx;
		padding-top: 40rpx;
		padding-bottom: 40rpx;
		border: 1rpx solid #c8c7cc;
		border-radius: 5rpx;
		text-align: center;
		font-size: 48rpx;
		position: relative;
	}

	.answer-box {
		width: 100%;
		position: relative;
	}

	.answer {
		width: 100%;
		padding: 5rpx;
		padding-top: 20rpx;
		padding-bottom: 20rpx;
		border: 1rpx solid #c8c7cc;
		border-radius: 5rpx;
		margin-top: 10rpx;
	}

	button {
		width: 60%;
	}

	.active {
		background-color: #00AAFF;
		color: #F8F8F8;
	}
</style>
