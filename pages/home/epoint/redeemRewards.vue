<template>
	<view class="content" style="width: 100%;height: 100%;">
		<view style="width: 100%;height: 120rpx;background: #FFFFFF;" class="flex">
			<text style="font-size: 38rpx;">My epoint<text style="padding: 0 10px;font-size: 40rpx;color: #BD2F35;font-weight: bold;">{{epoint}}</text>ePoints</text>
		</view>

		<view style="width: 90%;height: 70%;background: #007AFF"></view>

		<view style="width: 90%;height: 1px;background: #C0C0C0;margin-top: 10px;"></view>

		<view style="padding: 10px 0px;width: 90%;" class="content">
			<view>
				<text style="font-size: 30rpx;">Number of coupons
					<text style="padding: 0px 8px;font-weight: bold;font-size: 35rpx;">{{coupons}}</text>
				</text>
			</view>

			<view style="width: 100%;display: flex;flex-direction: row;justify-content: space-between;align-items: center;margin-top: 30rpx;">
				<view class="flex" style="width: 37%;">
					<view @tap="minus" class="flex" style="width: 90rpx;height: 70rpx;border-top-left-radius: 25px;border-bottom-left-radius: 25px;border:1px #E98689 solid;margin-right: 20rpx;">
						<text style="font-size: 60rpx;color:#E98689 ;padding-bottom: 5px;">-</text>
					</view>

					<view @tap="add" class="flex" style="width: 90rpx;height: 70rpx;border-top-right-radius: 25px;border-bottom-right-radius: 25px;border:1px #E98689 solid;background: #E98689;">
						<text style="font-size: 60rpx;color:#FFFFFF ;padding-bottom: 5px;">+</text>
					</view>

					<!-- 	<button plain="true" style="color: #E98689;border:1px #E98689 solid;border-top-left-radius: 25px;border-bottom-left-radius: 25px;font-weight: bold;font-size: 70rpx;line-height: 70rpx;">-</button>
					<button style="border-top-right-radius: 25px;border-bottom-right-radius: 25px;font-weight: bold;font-size: 56rpx;line-height: 70rpx;background: #E98689;color: #FFFFFF;">+</button> -->
				</view>
				<view>
					<button style="background:#E41F30 ;width: 300rpx;color: #FFFFFF;font-size: 35rpx;font-weight: bold;">Redeem</button>
				</view>



			</view>


		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				epoint: '2,500',
				coupons: 0
			}
		},
		methods: {
			minus() {
				if (this.coupons == 0) {
					uni.showToast({
						title: '不能在减了!',
						icon: 'none'
					});
				} else {
					this.coupons--
				}
			},
			add: function() {
				this.coupons++
			}
		},
	}
</script>

<style>
	page {
		width: 100%;
		height: 100%;
		background: #F6F6F6;
	}

	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.flex {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}
</style>
