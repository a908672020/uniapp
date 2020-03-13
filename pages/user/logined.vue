<template>
	<view >
		<view class="my" style="background: url(../../static/pic/logined.png);">
			<view class="mypic"><image src="../../static/pic/loginpic.png" mode="aspectFit"></image></view>
			<view class="mes">
				<text class="username">123123123{{username}}</text>
				<view class="Uvalue">
					<view style="width: 100vw;height: auto;">
						<text >当前U值</text><image src="../../static/pic/info.png" mode=""></image>
					</view>
					<view  style="width: 100vw;height: auto;">
						<text class="uvalue">{{uvalue}}</text>
					</view>
					<view  style="width: 100vw;height: auto;">
						<text @click="check()">点击查看会员权益></text>
					</view>
				</view>
			</view>
		</view>
		<view style="margin-top: 400upx;width: 100vw;">	
		<view class="warp">
			<view class="example-body">
				<uni-grid :column="3" :highlight="true" @change="change">
					<uni-grid-item v-for="(item, index) in list" :index="index" :key="index">
						<view class="grid-item-box">
							<image :src="item.url" class="image" mode="aspectFill" />
							<text class="text">{{ item.text }}</text>
						</view>
					</uni-grid-item>
				</uni-grid>
			</view>
		</view>
		</view>
		<view class="myservice">
			<view class="ser_title"><text>我的服务</text></view>
			<view class="warp">
				<view class="example-body">
					<uni-grid :column="3" :highlight="true" @change="change2">
						<uni-grid-item v-for="(item2, index2) in list2" :index="index2" :key="index2">
							<view class="grid-item-box">
								<image :src="item2.url" class="image" mode="aspectFill" />
								<text class="text">{{ item2.text }}</text>
							</view>
						</uni-grid-item>
					</uni-grid>
				</view>
			</view>
		</view>
		<view class="logout" >
			<button style="background-color: #FFFFFF;" type="default" hover-class="none" @click="logout()"><text>切换账号</text></button>
		</view>
	</view>
</template>

<script>
	import uniSection from '@/components/uni-section/uni-section.vue'
	import uniGrid from '@/components/uni-grid/uni-grid.vue'
	import uniGridItem from '@/components/uni-grid-item/uni-grid-item.vue'
	import uniBadge from '@/components/uni-badge/uni-badge.vue'
	export default{
		components:{
			uniSection,
			uniGrid,
			uniGridItem,
			uniBadge
		},
		data(){
			return{
				pro:25,
				uvalue:200,
				dynamicList: [],
				list: [{
						url: '../../static/icons/myorder.png',
						text: '我的订单',
					},
					{
						url: '../../static/icons/exchange.png',
						text: '退货退款',
					},
					{
						url: '../../static/icons/changefood.png',
						text: '我的换货',
					},
					{
						url: '../../static/icons/label.png',
						text: '提货凭证',
					},
					{
						url: '../../static/icons/orderrec.png',
						text: '订单回收'
					},
					{
						url: '../../static/icons/point.png',
						text: '更多敬请期待'
					}
					
				],
				list2: [{
						url: '../../static/icons/coupon.png',
						text: '优惠卷',
					},
					{
						url: '../../static/icons/heart.svg',
						text: '收藏夹',
					},
					{
						url: '../../static/icons/message.png',
						text: '站内信',
					},
					{
						url: '../../static/icons/mymessage.png',
						text: '个人资料',
					},
					{
						url: '../../static/icons/addbook.png',
						text: '地址簿'
					},
					{
						url: '../../static/icons/point.png',
						text: '更多敬请期待'
					}
					
				]
			}
		},
		methods:{
			check(res){
				console.log("您好！")
			},
			change(e) {
				let {index} = e.detail
				this.list[index].badge && this.list[index].badge++
				let t = this.list[index].text
				uni.showToast({
					// title: `点击第${index+1}个宫格`,
					title: `${t}`,
					icon: 'none'
				})
			},
			add() {
				if (this.dynamicList.length < 6) {
					this.dynamicList.push({
						url: `/static/c${this.dynamicList.length+1}.png`,
						text: `Grid ${this.dynamicList.length+1}`,
						color: this.dynamicList.length % 2 === 0 ? '#f5f5f5' : "#fff"
					})
				} else {
					uni.showToast({
						title: '最多添加6个',
						icon: 'none'
					});
				}
			},
			del() {
				this.dynamicList.splice(this.dynamicList.length - 1, 1)
			},
			logout(){
				uni.getStorageInfo({
					success:(res) =>{
						let js_code = res.code;
						uni.removeStorage({
						key:res.code,
						success: () => {
							console.log("success");
					}
				})
					}
				})
				
				uni.reLaunch({
					url:'user'
				})
			}
		}
	}
</script>

<style>
	progress{
		width: 70vw;
	}
	border::after{
		border: none;
	}
.my {
	height: 400upx;
	width: 100vw;
	align-items: center;
	padding: 0px 5vw;
	position: absolute;
	top: 0;
	left: 0;
	color: #FFFFFF;
}
.my text{
	margin-bottom: 50upx;
}
.mypic {
	height: 200upx;
	width: 200upx;
	border-radius: 50vw;
	background-color: #ffffff;
	margin-top: 100upx;
	float: left;
	margin-right: 5vw;
}
.mypic image {
	height: 120upx;
	width: 120upx;
	margin-top: 40upx;
	margin-left: 40upx;
}
.mes{height: 300upx;margin-top: 50upx;}
.mes button{border: none;background-color: none;}
.username{font-size: 1em;}
.Uvalue{font-size: 0.6em;margin-top: 30upx;}
.Uvalue image{
	height: 24upx;
	width: 24upx;
}
.uvalue{
	font-size: 50upx;
}
/* .warp{
	margin-top:400upx ;
} */
.myservice{
	width: 100vw;
	background-color: #FFFFFF;
	margin-top: 35upx;
}
.ser_title{
	height: 120upx;
}
.ser_title text{
	line-height: 120upx;
	margin-left: 50upx;
}
.logout{
	width: 100vw;
	height: 120upx;
	background-color: #FFFFFF;
	margin-top: 35upx;
	text-align: center;
}
.logout text{
	text-align: center;
	line-height: 120upx;
}
	
	
	
	/* #ifndef APP-NVUE */
		page {
			display: flex;
			flex-direction: column;
			box-sizing: border-box;
			background-color: #efeff4;
			min-height: 100%;
			height: auto;
		}
	
		view {
			font-size: 14px;
			line-height: inherit;
		}
	
		.example {
			padding: 0 15px 15px;
		}
	
		.example-info {
			padding: 15px;
			color: #3b4144;
			background: #ffffff;
		}
	
		.example-body {
			flex-direction: row;
			flex-wrap: wrap;
			justify-content: center;
			padding: 0;
			font-size: 14px;
			background-color: #ffffff;
		}
	
		/* #endif */
		.example {
			padding: 0 15px;
		}
	
		.example-info {
			/* #ifndef APP-NVUE */
			display: block;
			/* #endif */
			padding: 15px;
			color: #3b4144;
			background-color: #ffffff;
			font-size: 14px;
			line-height: 20px;
		}
	
		.example-info-text {
			font-size: 14px;
			line-height: 20px;
			color: #3b4144;
		}
	
	
		.example-body {
			flex-direction: column;
			background-color: #ffffff;
		}
	
		.word-btn-white {
			font-size: 18px;
			color: #FFFFFF;
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
			background-color: #007AFF;
		}
	
		.word-btn--hover {
			background-color: #4ca2ff;
		}
	
	
		.image {
			width: 50rpx;
			height: 50rpx;
		}
	
		.text {
			font-size: 26rpx;
			margin-top: 10rpx;
		}
	
		.example-body {
			/* #ifndef APP-NVUE */
			display: block;
			/* #endif */
		}
	
		.grid-dynamic-box {
			margin-bottom: 15px;
		}
	
		.grid-item-box {
			flex: 1;
			/* position: relative;
	*/
			/* #ifndef APP-NVUE */
			display: flex;
			/* #endif */
			flex-direction: column;
			align-items: center;
			justify-content: center;
			padding: 15px 0;
		}
	
		.grid-dot {
			position: absolute;
			top: 5px;
			right: 15px;
		}
</style>
