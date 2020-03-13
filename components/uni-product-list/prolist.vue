<template>
	<view class="uni-product-list">
		<view class="uni-product" v-for="(product, index) in productList" :key="index" @click="getdetial(index)">
			<view class="image-view fl"><image class="uni-product-image" mode="scaleToFill" :src="product.pciture"></image></view>
			<view class="des-view fl">
				<text class="uni-product-tip">{{ product.tip }}</text>
				<view class="uni-product-title">{{ product.title }}</view>
				<view class="uni-product-des">{{ product.des }}</view>

				<view class="uni-product-price">
					<text class="uni-product-price-original">￥{{ product.favourPrice }}</text>
				</view>
			</view>
			<view class="clear"></view>
		</view>
	</view>
</template>

<script>
name: 'prolist';
export default {
	props: {
		productList: {
			type: Array,
			default() {
				return [];
			}
		}
	},
	data() {
		return {
			renderImage: false
		};
	},
	onLoad() {},
	methods: {
		getdetial(i) {
			uni.showLoading({
				title: '将前往详情页面',
				duration: 2000,
				mask: true
			});
		}
	}
};
</script>

<style lang="scss" scoped>
.uni-product-list {
	width: 100vw;
	height: auto;
	padding-left: 50upx;
}
.image-view {
	height: 50vw;
	width: 50vw;
	margin: 12upx 0;
}
.uni-product-image {
	height: 48vw;
	width: 48vw;
}
.des-view {
	width: 40vw;
	margin-left: 30upx;
}
.uni-product-tip {
	background-color: #fe0005;
	color: #ffffff;
	font-weight: 600;
	font-size: 20upx;
	text-align: center;
	padding: 5upx 7upx 5upx 7upx;
}
.uni-product-title {
	margin-top: 20upx;
	color: #000000;
	font-weight: 600;
	font-size: 24upx;
}
.uni-product-price-original {
	color: #fe0005;
	font-weight: 600;
	font-size: 20upx;
}
</style>
