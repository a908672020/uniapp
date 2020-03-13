<template>
	<view>
		<view class="line"></view>
		<view class="cart-list"  v-for="(pro,i) in carlist"  :key="i" >
			<view class="cart_list_top">
				<label>
					<checkbox :value="c1" style="transform:scale(0.7)" /><text style="float: right;">修改配送方式</text>
				</label>
			</view>
			<view class="cart_list_mid" v-for="(pro,i) in carlist"  :key="i" @click="getdetial(i)">
				<view class="cart_pic "><image  :src="pro.pic" mode="aspectFit"></image></view>
				<view class="cart_des ">
					<view class="cart-des-title">{{pro.title}}</view>
					<view class="uni-des-color">{{ pro.color }}</view>
					<view class="uni-des-size">{{ pro.size }}</view>
					<view class="uni-des-sup">{{pro.sup}}</view>
					¥<view class="uni-des-price" >{{pro.price}}</view>
				</view>
				
			</view>
			<view class="clear"></view>
			<view class="cart_list_bottom">
				<image src="../static/icons/subtract.png" class="sub" @click="sub()" mode="scaleToFill"></image>
				<input type="text" class="num" :value="num" />
				<image src="../static/icons/add.png" class="add" @click="add()" mode="scaleToFill"></image>
			</view>
			
		</view>
		
	</view>
</template>

<script>
	name:'cartlist'
	export default {
		props: {
			
			carlist: {
				type: Array,
				default() {
					return [];
				}
			}
		},
		data() {
			return {
				num:1,reprice:0,
			};
		},
		methods: {
			getdetial(i) {
				uni.showLoading({
					title: '将前往详情页面',
					duration: 2000,
					mask: true
				});
			},
			add(){
				this.num +=1;
				// console.log(this.num);
				this.reprice = this.num * pro.price;
				return num
			},
			sub(){
				if(this.num <= 0){
					this.num = 0;
				}
				 else{this.num -= 1;}
				// console.log(this.num);
				  return num;
			}
		}
	}
</script>

<style>
.line{
	background-color: #d3d3d3;
	height: 3upx;
	width: 90vw;
	margin-left: 5vw;
	margin-top: 10upx;
}
.cart-list{
	height: 750upx;
	width: 100vw;
	background-color: #FFFFFF;
}
.cart_list_top{
	margin-right: 5vw;margin-left: 5vw;
}
.cart_list_mid{
	width: 90vw;
	margin-left: 5vw;
}
.cart_pic{height: 40vw;width: 40vw;float: left;}
.cart_pic image{
	height: 40vw;
	width: 40vw;
}
.cart_des{
	width:45vw;
	height: auto;
	margin-left: 5vw;
	margin-top: 5upx;
	float: left;
	line-height: 50upx;
}
.cart_list_bottom{
	width:45vw;
	height: auto;
	margin-left: 5vw;
	margin-top: 5upx;
	float: left;
}
.sub,.add,.num{
	width: 5vw;
	height: 5vw;
	margin-right: 3vw;
	float: left;
	align-items: center;
}
/* .sub image,.add image{
	width: 5vw;
	height: 5vw;
} */
</style>
