<template>
	<view class="bg">
		<!-- <view class="bg" :style="{ height: h + 'px', width: w + 'px' }"> -->
			<view class="con" :style="{ height: 0.9 * h + 'px' }">
				<view class="center">
					<image src="../../static/pic/loginpic.png" mode="aspectFit" class="loginpic"></image>
					<view class="user-btn-group">
						<button type="default" open-type="getUserInfo" class="weixinbtn" hover-class="none" @click="wxlogin"><image src="../../static/icons/wxpic.png" mode="aspectFit" class="wxpic"></image><text>微信登陆</text></button>
						<button type="default" class="phone" hover-class="none" @click="phonelogin"><text>手机号登录</text></button>
					</view>
				</view>
			</view>
		<!-- </view> -->
	</view>
</template>

<script>

export default {
	components: {
		
	},
	data() {
		return {
			h: 0,
			w: 0,
			
			
		};
	},

	onLoad() {
		
		uni.getSystemInfo({
			success: res => {
				// console.log(res.windowHeight);
				// console.log(res.windowWidth);
				this.h = res.windowHeight;
				this.w = res.windowWidth;
				
			}
		});
	},

	methods: {
		phonelogin(){
			uni.navigateTo({
				url: './phonelogin',

			});
		},
		wxlogin(){
			uni.login({
				provider:'weixin',
				success: (res) => {
					let js_code = res.code;
					console.log(js_code);
					uni.getUserInfo({
						provider:'weixin',
						success: (userres) => {
							uni.setStorage({
								key:res.code,
							})
						},
					})
					
				},
			})
			uni.navigateTo({
				url: './logined',
			});
		},
		
	}
};
</script>

<style>

.bg {
	background-color: #f4f4f4;
	padding: 10vw 5vw 10vw 5vw;
}
.bg text{
	font-size: 14px;
}
.con {
	background-color: #ffffff;
	width: 90vw;
	box-shadow: 1px 5px 5px #e3e3e3;
	text-align: center;
	display: flex;
	align-items: center;
}
.center{
	height: auto;
	width: auto;
	margin: 0 auto;
	align-self: center;
	align-items: center;
}
.loginpic {
	height: 100upx;
	width: 88upx;
}
.user-btn-group {
	width: 80vw;

}
.user-btn-group button{
	border-radius: 0px;
	background-color: #FFFFFF;
	height: 70upx;
	line-height: 70upx;
	text-align: center;
}
.weixinbtn {
	border: 1px solid #4cd964;
	margin-top: 60upx;

}
.weixinbtn text{
	margin-top: 0px;
}
.wxpic{
	height: 60upx;
	width: 60upx;
	margin-right: 10upx;
}
.phone{
	border: 1px solid #333333;
	margin-top: 20upx;	
}
.example-body {
	flex-direction: column;

	background-color: #ffffff;
}

.word-btn-white {
	font-size: 18px;
	color: #ffffff;
}

.word-btn {
	/* #ifndef APP-NVUE */
	display: flex;
	/* #endif */
	flex-direction: row;
	align-items: center;
	justify-content: center;
	border-radius: 6px;
	height: 48px;
	margin: 15px;
	background-color: #007aff;
}

.word-btn--hover {
	background-color: #4ca2ff;
}

.example-body {
	padding: 0;
	flex-direction: row;
	/* flex-wrap: wrap; */
	/* align-items: center;
 */
	/* justify-content: center;
 */
}

.uni-right {
	flex-direction: row;
	flex-wrap: nowrap;
	align-items: center;
	color: #666;
}

.uni-right-text {
	font-size: 28rpx;
}

.switch {
	transform: scale(0.8);
	margin-left: 5px;
}

.icon-item {
	/* #ifndef APP-NVUE */
	display: flex;
	box-sizing: border-box;
	/* #endif */
	width: 24upx;
	text-align: center;
	flex-direction: column;
}

.icon-item-text {
	font-size: 24rpx;
	text-align: center;
}
</style>
