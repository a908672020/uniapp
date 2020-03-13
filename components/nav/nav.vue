<template>
	<view>
		<view class="navabr">
			<image src="../../static/icons/navl.png" mode=""></image>
			<view class="navr">
				<image src="../../static//icons/heart.svg" mode=""></image>
			<image src="../../static/icons/searchpic.svg" mode="" @click="togglePopup('top', 'popup')">
				<uni-popup ref="showpopup" :type="type" @change="change">
					<uni-search-bar radius="5" placeholder="自动显示隐藏" clearButton="auto" cancelButton="auto" @confirm="search" />
					<view class="taggroup"><uni-tag text="标签"></uni-tag></view>
				</uni-popup>
			</image>
			<image src="../../static/icons/Scan.svg" mode=""></image>
			</view>
			
			<!-- <view class="search">
				<view type="default" class="item" v-for="(value, index) in iconType" :key="index" ><icon :type="value" size="20" color="#000000" /></view>
				<uni-popup ref="showpopup" :type="type" @change="change">
					<uni-search-bar radius="5" placeholder="自动显示隐藏" clearButton="auto" cancelButton="auto" @confirm="search" />
					<view class="taggroup"><uni-tag text="标签"></uni-tag></view>
				</uni-popup>
			</view> -->
		</view>
		
	</view>
</template>

<script>
import uniTag from '@/components/nav/uni-tag/uni-tag.vue';
import uniSearchBar from '@/components/nav/uni-search-bar/uni-search-bar.vue';
import uniSection from '../../components/uni-section/uni-section.vue';
import uniPopup from '@/components/nav/uni-popup/uni-popup.vue';
import uniIcons from '@/components/uni-icons/uni-icons.vue';
export default {
	name: 'navbar',
	components: {
		uniSearchBar,
		uniSection,
		uniPopup,
		uniIcons,
		uniTag
	},
	data() {
		return {
			iconType: ['search']
		};
	},
	onLoad: function() {
		// #ifdef APP-PLUS|| MP-WEIXIN
		this.iconType = ['success', 'success_no_circle', 'info', 'warn', 'waiting', 'cancel', 'download', 'search', 'clear'];
		// #endif
		// #ifdef MP-ALIPAY
		this.iconType = ['info', 'warn', 'waiting', 'cancel', 'download', 'search', 'clear', 'success', 'success_no_circle', 'loading'];
		// #endif
		// #ifdef MP-BAIDU
		this.iconType = [
			'success',
			'info',
			'warn',
			'waiting',
			'success_no_circle',
			'clear',
			'search',
			'personal',
			'setting',
			'top',
			'close',
			'cancel',
			'download',
			'checkboxSelected',
			'radioSelected',
			'radioUnselect'
		];
		// #endif
	},
	methods: {
		togglePopup(type, open) {
			switch (type) {
				case 'top':
					this.content = '顶部弹出 popup';
					break;

				case 'bottom':
					this.content = '底部弹出 popup';
					break;
				case 'center':
					this.content = '居中弹出 popup';
					break;
			}
			this.type = type;
			this.$nextTick(() => {
				this.$refs['show' + open].open();
			});
		}
	},
	onBackPress() {
		this.$refs['showpopup'].close();
		// #ifdef APP-PLUS
		plus.key.hideSoftKeybord();
		// #endif
	}
};
</script>

<style>
.navabr image {
	height: 50upx;
	width: 50upx;
	margin-right: 100upx;
}
input {
	width: 80%;
}
uni-tag {
	width: auto;
	border-radius: 15upx;
	float: left;
	margin-right: 24upx;
}


.button {
	flex: 1;
	margin: 10px 0;
}

.popup-content {
	/* #ifndef APP-NVUE */
	display: block;
	/* #endif */

	background-color: #fff;
	padding: 15px;
	font-size: 14px;
}
.navabr {
	height: 60upx;
	padding: 5upx 10%;
	display: flex;
	align-items: center;
	background-color: #f0f4f7;
	line-height: 60upx;
}
.navr{
	margin-top: 15upx;
	margin-left: 150upx;
	float: right;
}
.navr image{
	margin-right: 40upx;
}

.taggroup {
	padding: 0upx 20upx;
	background-color: #ffffff;
}

</style>
