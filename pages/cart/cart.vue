<template>
	<view class="bg">
		<view class="cart_top pd05">
			<label>
				<checkbox :value="all" style="transform:scale(0.7)" />
				<text>全选</text>
			</label>
			<text style="text-decoration:underline ;float: right;">编辑全部</text>
		</view>

		<cartlist @totalpay="totalpay" :carlist="carlist"></cartlist>
		<view class="totalprice">
			<text class="fl" style="margin-left: 5vw;">合计：</text>
			<text class="fl" style="color:#fe0000;">￥{{ total }}</text>
			<text class="fl" style="color:#666666;font-size: 20upx;margin-left: 10upx;">不含运费</text>
			<button type="default" class="payable" :class="isactive">结算</button>
		</view>
	</view>
</template>

<script>
import cartlist from '../../components/cart_list.vue';
export default {
	components: { cartlist },
	data() {
		return {
			total: 0.0,
			carlist: [
				{
					pic: '../static/listmodel/2.png',
					title: '男装 长袖',
					color: '墨绿',
					size: '175/90B',
					sup: '支持30天无理由退货',
					price: '199'
				}
			]
		};
	},
	methods: {
		totalpay(pay){
			console.log(pay);
			this.total = this.pay;
		}
	}
};
</script>

<style>
.pd05 {
	padding: 0px 5vw;
}
.bg {
	background-color: #f4f4f4;
	font-size: 24upx;
}
.fl {
	float: left;
}
.cart_top {
	background-color: #ffffff;
	height: 100upx;
	line-height: 100upx;
}
.product {
	background-color: #ffffff;
	margin-top: 30upx;
	padding-top: 10upx;
}
.totalprice {
	width: 100vw;
	border-top: 1px solid #d3d3d3;
	position: fixed;
	bottom: 0;
	font-size: 30upx;
	line-height: 50upx;
}
.payable {
	float: right;
	width: 20vw;
	height: 50upx;
	line-height: 50upx;
	text-align: center;
	font-size: 30upx;
	margin-right: 5vw;
}
</style>
