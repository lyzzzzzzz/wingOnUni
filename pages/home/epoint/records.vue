<template>
	<view class="content">
		<view style="width: 100%;height: 120rpx;background: #FFFFFF;" class="flex">
			<text style="font-size: 38rpx;">My epoint<text style="padding: 0 10px;font-size: 40rpx;color: #BD2F35;font-weight: bold;">{{epoint}}</text>epoint</text>
		</view>

		<view style="width: 100%;" class="flex">
			<p style="width: 95%;font-size: 32rpx;text-align: center;padding: 10px 0px;">Latest 30 ePoint Records(Including
				refunded and returned transactions)</p>
		</view>

		<view class="uni-list" style="background: #F6F6F6;">
			<view class="uni-list-cell" hover-class="uni-list-cell-hover" v-for="(item,index) in list" :key="index" style="width: 90%;margin: auto;">
				<view style="width: 100%;">
					<text style="font-size: 24rpx;color:#C0C0C0">{{item.time}}</text>
					<view style="width: 100%;" class="listContent">
						<p style="width: 70%;word-wrap: break-word;font-size: 35rpx;">{{item.content}}</p>
						<p style="width: 25%;word-wrap: break-word;color:#BD2F35 ;font-size: 30rpx;">+{{item.epoint}}&nbsp;ePoints</p>

					</view>
				</view>

			</view>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				epoint: "2,500",
				list: [{
						time: '11/10/2019 16:07:53',
						content: 'content content content',
						epoint: "10,002222"
					},
					{
						time: '11/10/2019 16:07:53',
						content: 'content content content',
						epoint: "10,002222"
					}
				]
			}
		},
	}
</script>

<style>
	page {
		width: 100%;
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

	.listContent {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		/* align-items: center; */
	}
</style>
