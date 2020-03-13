<template>
	<view class="bg">
		<view class="con" :style="{ height: 0.9 * h + 'px' }">
			<view class="contast">
				<view class="text"><text style="font-weight: 600;">联系我们</text></view>
				<view class="text"><text>在线客服</text></view>
				<button type="default">联系客服</button>
				<view class="text"><text>服务时间：24小时 \n 客服热线：000-123-1111</text></view>
				<button type="default">拨打电话</button>
				<view class="text"><text>服务时间：09：00-21：00</text></view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				h:0,
			}
		},
		onLoad() {
				uni.getSystemInfo({
					success: res => {
						// console.log(res.windowHeight);
						// console.log(res.windowWidth);
						this.h = res.windowHeight;
						
					}
				});			
		},
		methods: {
			
		}
	}
</script>

<style>
	.bg {
		background-color: #f4f4f4;
		padding: 5vw;
	}
.con {
	background-color: #ffffff;
	width: 90vw;
	box-shadow: 1px 5px 5px #e3e3e3;
	text-align: center;
	display: flex;
	align-items: center;
}
.contast{
	text-align: left;
	padding-left: 5vw;
}
.text{
	margin-top: 24upx;
	margin-bottom: 24upx;
}
.contast button{
	background-color: #333333;
	color: #FFFFFF;
	text-align: center;
	height: 100upx;
	line-height: 100upx;
	width: 80vw;
	font-size: 1em;
}
</style>
