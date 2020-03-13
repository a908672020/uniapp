<template>
	<view class="bg">
			<view class="con" :style="{ height: 0.9 * h + 'px' }">				
					<image src="../../static/pic/loginpic.png" mode="aspectFit" class="phonelogin" ></image>
					<view class="phonumber">
						<input type="number" v-mode="number" class="fl" placeholder="手机号" />
					</view>
					<view class="clear"></view>
					<view class="vercode">
						<input type="number" class="fl code" placeholder="验证码" />
						<view class="clear"></view>
						<button type="default" class="getcode" @click="check()"><text>获取验证码</text></button>
					</view>
					<view class="clear"></view>
					<button type="default" class="login" :disabled="disabled"><text>登录</text></button>
					
			</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				h: 0,
				w: 0,
				disabled:true
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: res => {
					console.log(res.windowHeight);
					console.log(res.windowWidth);
					this.h = res.windowHeight;
					this.w = res.windowWidth;
				}
			});
		},
		methods: {
			check(str){
			 const self = this; 
			 if(/^((1[3,5,8][0-9])|(14[5,7])|(17[0,6,7,8])|(19[7]))\d{8}$/.test(self.number)){
				 return this.disabled = true,
				   self.$toast({
				             message: "电话号码格式错误",
				             position: "bottom"
				             
				           })
			 }else{
				 return this.disabled = false
			 }
			}
		}
	}
</script>

<style>
	.bg {
		background-color: #f4f4f4;
		padding: 10vw 5vw 10vw 5vw;
	}
	.bg text{
		font-size: 14px;
	}
.con{
	background-color: #ffffff;
	width: 90vw;
	box-shadow: 1px 5px 5px #e3e3e3;
	text-align: center;
	display: flex;
}
.phonelogin {
	height: 100upx;
	width: 88upx;
	position: absolute;
	top: 30%;
	left: 50%;
	margin-left: -44upx;
}
.phonumber{
	width: 80vw;
	height: 50upx;
	position: absolute;
	top: 70vw;
	border-bottom:1px solid #F1F1F1;
	left: 10vw;
}
.vercode{
	width: 80vw;
	height: 50upx;
	border-bottom:1px solid #F1F1F1;
	position: absolute;
	top: 80vw;
	left: 10vw;
}
.code{
	width: 40vw;
	height: 48upx;
	line-height:48upx;
	text-align: left;
	border: none;
}
.getcode{
	width: 30vw;
	height:40upx;
	line-height: 40upx;
	padding: 0px;
	float: right;
	margin-top: -45upx;
}
.phonumber input{
	margin-bottom: 40upx;
	width: 80vw;
	height: 48upx;
	line-height:48upx;
	text-align: left;
	border: none;
}
.login{
	width: 80vw;
	height: 70upx;
	line-height: 70upx;
	position: absolute;
	top: 90vw;
	left: 10vw;
}
</style>
