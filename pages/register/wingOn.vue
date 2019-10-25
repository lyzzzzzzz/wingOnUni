<template>
	<view style="height: 100%;width: 100%;display: flex;flex-direction: column;justify-content: center;align-items: center;">
		<view class="status_bar">
			<!-- 这里是状态栏 -->
		</view>
		<view style="height: 44px;background: #E41F30;width: 100%;display: flex;flex-direction: row;justify-content: space-between;align-items: center;">
			<image src="../../static/wingOn/bars.png" style="height: 60rpx;width: 70rpx;" mode="aspectFit"></image>
			<image src="../../static/wingOn/rigisterTitle.png" style="width: 500rpx;height: 60rpx;" mode="aspectFit"></image>
			<view style="height: 60rpx;width: 70rpx;"></view>
		</view>
		<view class="content">
			<text style="color: #E41F30; font-size:55rpx;font-weight: bold;margin-top: 30px;">Enjoy Fabulous Offers</text>
			<view class="btns">
				<button style="background: #FFFFFF;color: #E41F30;border-color: #E41F30;" class="btn" type="default" plain="true">Join
					Us</button>
				<button style="background:#E41F30 ;color: #FFFFFF;" class="btn" @click="toLogin">Login</button>
			</view>

		</view>
	</view>
</template>

<script>
export default {
	methods: {
		toLogin() {
			uni.navigateTo({
				url: '../login/login'
			});
		}
	},
}
</script>

<style>
	page {
		height: 100%;
		width: 100%;
	}
	.status_bar {
		height: var(--status-bar-height);
		width: 100%;
		background: #E41F30;
	}

	.content {
		background-image: url(https://raw.githubusercontent.com/lyzzzzzzz/img/master/wingon_background.png);
		background-size: cover;
		background-position: 50% 0px;
		background-repeat: no-repeat no-repeat;
		width: 100%;
		flex: 1;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: center;
	}

	.btns {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		width: 100%;
		margin-bottom: 40px;
	}

	.btn {
		width: 120px;
		height: 50px;
		font-weight: bold;
	}
</style>
