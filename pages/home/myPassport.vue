<template>
	<view class="content">
		<text style="margin-top: 80rpx;font-weight: bold;font-size: 38rpx;">Scan to Pay and Redeem epoint</text>
		<view style="margin-top: 100rpx;">
			<image :src="img" style="width: 300rpx;height: 300rpx;"></image>
		</view>
		<text style="margin-top: 100rpx;font-size: 35rpx;">My MenberShip Number</text>
		<text style="margin-top: 40rpx;font-size: 35rpx;font-weight: bold;">{{menberShip}}</text>
	</view>
</template>

<script>
	import QR from "../../common/js/wxqrcode.js"
	export default {
		data() {
			return {
				qrcode: '二维码', // 要生成的二维码值
				menberShip: '1111111111111111111111',
				img: null
			}
		},
		methods: {

		},
		onLoad: function() {
			var img = QR.createQrCodeImg(this.menberShip, {
				size: parseInt(300)
			})
			this.img = img
		}
	}
</script>

<style>
	page {
		height: 100%;
		width: 100%;
	}

	.content {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-items: center;
	}
</style>
