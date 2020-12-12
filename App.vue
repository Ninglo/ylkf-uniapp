<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onHide: function() {
			console.log('App Hide')
		},
		onShow: function (object) {
		  var unionid = uni.getStorageSync('unionid');//用户唯一id
		  if(unionid == ''){
		    uni.showModal({
		      title: '提示',
		      content: '请您先授权登录',
		      showCancel: true,
		      success (res){
		        if (res.confirm) {
					uni.redirectTo({
						url:"../login/login",
						success() {
							console.log("成功跳转")
						},
						fail(e) {
							console.log("失败")
							console.log(e)
						}
					})
					console.log(res)
		            console.log('用户点击确定')
		          
		        }else{
					
				} 
		      }
		    })
		  }
		},
	}
</script>

<style>
	/*每个页面公共css */
	view{
		font-size: 35upx;
	}
</style>
