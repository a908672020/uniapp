<template>
	<view class="body">
		<navbar></navbar>
		<view class="banner">
			<view class="ban_top" :class="{fix:isFixed}" id="bantop" >
					<button type="" class="ban_topl bgw fl"  hover-class="none"><text>新品 · 活动</text></button>
					<button type="" class="ban_topr bgw fl"  hover-class="none"><text>商城</text></button>	
			</view>
			<view class="content">
					<special-banner :banner-list="bannerList" :swiper-config="swiperConfig" ></special-banner>
			</view>
		</view>
		<view class="btngroup">
			<button type="" class="bgw fl"><image src="../../static/pic/model.png" mode="aspectFit" class="fl"></image><text>活力上新</text></button>
			<button type="" class="bgw fl"><image src="../../static/pic/model2.png" mode="aspectFit" class="fl"></image><text>人气特惠</text></button>
			<button type="" class="bgw fl"><image src="../../static/pic/model3.png" mode="aspectFit" class="fl"></image><text style="color: #a46a3a;">爆品情报站</text></button>
			<button type="" class="bgw fl"><image src="../../static/pic/model4.png" mode="aspectFit" class="fl"></image><text style="color: #a46a3a;">2020春夏系列</text></button>
		</view>
		<view class="clear"></view>
		<prolist :productList="productList"></prolist>
	</view>
</template>

<script>
import uniSection from '../../components/uni-section/uni-section.vue';
import navbar from '../../components/nav/nav.vue';
import specialBanner from '../../components/swiper/specialBanner.vue';
import prolist from '../../components/uni-product-list/prolist.vue';
export default {
	components: { navbar,specialBanner,prolist },
	data() {
		return {
			isFixed:false,
			scrollnum: 0,
			//轮播图
			bannerList: [{
				picture: '../../static/pic/t1.jpg',
				title: '',
				description: '',
				path: ''
			}, {
				picture: '../../static/pic/t2.jpg',
				title: '',
				description: '',
				path: ''
			}, {
				picture: '../../static/pic/t3.jpg',
				title: '',
				description: '',
				path: ''
			}, {
				picture: '../../static/pic/t4.jpg',
				title: '',
				description: '',
				path: ''
			}],
			swiperConfig: {
				indicatorDots: true,
				indicatorColor: 'rgba(255, 255, 255, .4)',
				indicatorActiveColor: 'rgba(255, 255, 255, 1)',
				autoplay: false,
				interval: 3000,
				duration: 300,
				circular: true,
				previousMargin: '58rpx',
				nextMargin: '58rpx'
			},
			//产品列表
			productList:[{
                        pciture: '/static/listmodel/1.png',
                        title: '经典长袖T恤',
						des:'宽松舒适  春季亲肤内搭',
                        favourPrice: 79,                        
                        tip: '活力焕新'
                    },
                    {
                        pciture: '/static/listmodel/4.png',
                        title: '经典长袖T恤',
						des:'宽松舒适  春季亲肤内搭',
                        favourPrice: 3499,                       
                        tip: '优惠'
                    },
                    {
                        pciture: '/static/listmodel/2.png',
                        title: '经典长袖T恤',
						des:'宽松舒适  春季亲肤内搭',
                        favourPrice: 12999,
                        tip: '秒杀'
                    },
                    {
                        pciture: '/static/listmodel/3.png',
                        title: '经典长袖T恤',
						des:'宽松舒适  春季亲肤内搭',
                        favourPrice: 999,
                        tip: '秒杀'
                    }   
                ],
		};
	},
	onLoad() {
		uni.startPullDownRefresh();
		const query = uni.createSelectorQuery().in(this);
		
	},
	onPullDownRefresh(){
		  setTimeout(function () {
		            uni.stopPullDownRefresh();  //停止下拉刷新动画
		        }, 1000);

	},
	onPageScroll(res){
		let scrollnum = res.scrollTop;
		console.log(scrollnum);
		if(scrollnum>=60){
			return this.isFixed = true;
		}else{
			return this.isFixed =  false;
		}
	},

	methods: {
		select(item) {
			this.sel = item.id;
		},
		// fixtop(onPageScroll){
		// 	const query = uni.createSelectorQuery().in(this);
		// 	query.select('#bantop').style.position = 'fixed';
		// 	query.select('#bantop').style.top = 0;
		// },
	},
	
};
</script>

<style lang="less">
.clear{
	clear: both;
}
.fl{
	float: left;
}
.fr{
	float: right;
}
.bgw{
	background-color: #FFFFFF;
}
.body{
	background-color: #f1f5f8;
	
}
.banner {
	height: auto;
	width: 100vw;
}
.ban_top {
	height: 60upx;
	
}
.fix{
	width: 100vw;
	position: fixed;
	top: 0;
	z-index: 999;
}
.ban_topl {
	width: 50%;
	text-align: center;
	border-bottom: #fe0005;
}
.ban_topr {
	width: 50%;
	text-align: center;
}
.ban_top text {
	width: 100vw;
	line-height: 60upx;
	font-size: 24upx;
}

.content {
		width: 100vw;
		height: auto;
		
	}
.btngroup{
	padding-left: 5vw;
	width: 100vw;
	height: auto;
	margin-top: 150upx;
}
.btngroup button{
	width: 42vw;
	height: 100upx;
	margin-right: 5vw;
	background-color: #FFFFFF;
	text-align: right;
	margin-bottom: 20upx;
	border:1px solid #888888;
	overflow: visible;
}
.btngroup button text{
	font-size: 24upx;
	margin-bottom: 10upx;
	font-weight: 700;
}
.btngroup button image{
	width: 100upx;
	height: 120upx;
	position: absolute;
	margin-top: -20upx;
	left: 5vw;
}


</style>
