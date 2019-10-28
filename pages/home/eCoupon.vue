<template>
	<view>
		<uni-segmented-control :current="current" :values="items" @clickItem="onClickItem" style-type="text" active-color="#E41F30"
		 style="height: 70rpx;width: 90%;font-weight: bold;"></uni-segmented-control>


		<view>
			<!-- My Rewards -->
			<view v-show="current === 0" style="margin-top: 40rpx;">
				<scroll-view style="width: 100%;" scroll-y="true" show-scrollbar="false">
					<view v-for="item in list" :key="item.id" style="margin-bottom: 25rpx;">
						<view style="padding: 20rpx;border-radius: 15px;background: #FFFFFF;width: 90%;margin: auto;">
							<view style="display: flex;flex-direction: row;align-items: center;">
								<image :src="item.img" style="width: 90rpx;height: 90rpx;border-radius: 35px;"></image>
								<view style="margin-left: 20rpx;flex: 1;">
									<p style="width: 100%;word-break: break-word;color: #E41F30;font-size: 30rpx;font-weight: bold;">{{item.title}}</p>
									<view style="font-size: 31rpx;font-weight: bold;">({{item.active}})</view>
								</view>
							</view>
							<view style="width: 100%;">
								<p style="width: 100%;word-break: break-word;"> {{item.content}}</p>
							</view>
							<view style="margin-top: 20rpx;">
								<text style="color: #B2B2B2">Expiry Date:{{item.time}}</text>
							</view>
						</view>
					</view>
				</scroll-view>
			</view>

			<!-- e-Coupons -->
			<view v-show="current === 1" style="margin-top: 40rpx;">
				<scroll-view style="width: 100%;" scroll-y="true" show-scrollbar="false">
					<view v-for="item in couponList" :key="item.id" style="margin-bottom: 25rpx;">
						<view style="padding: 20rpx;border-radius: 15px;background: #FFFFFF;width: 90%;margin: auto;">
							<view style="display: flex;flex-direction: row;">
								<image :src="item.img" style="width: 90rpx;height: 90rpx;"></image>
								<view style="margin-left: 20rpx;flex: 1;">
									<p style="width: 100%;word-break: break-word;color: #E41F30;font-size: 30rpx;font-weight: bold;">{{item.title}}</p>
								
								</view>
							</view>
							<view style="width: 100%;">
								<p style="width: 100%;word-break: break-word;"> {{item.content}}</p>
							</view>
							<view style="margin-top: 20rpx;">
								<text style="color: #B2B2B2">Expiry Date:{{item.time}}</text>
							</view>
						</view>
					</view>
				</scroll-view>
			</view>

		</view>

	</view>


</template>

<script>
	import uniSegmentedControl from "../../components/uni-segmented-control/uni-segmented-control.vue"
	export default {
		components: {
			uniSegmentedControl
		},
		data() {
			return {
				items: ['My Rewards', 'e-Coupons'],
				current: 0,
				list: [{
						img: '../../static/logo.png',
						title: 'titletitletitletitletitle',
						content: 'contentcontentcontentcontentcontentcontentcontentcontentcontentcontentcontent',
						active: 'Expired',
						time: '26/10/2019'
					}
				],
				couponList:[{
						img: '../../static/logo.png',
						title: 'titletitletitletitletitle',
						content: 'contentcontentcontentcontentcontentcontentcontentcontentcontentcontentcontent',
						active: 'Expired',
						time: '26/10/2019'
					}]
							}
		},
		methods: {
			onClickItem(index) {
				if (this.current !== index) {
					this.current = index;
				}
			},
		},
	}
</script>

<style>
	page {
		width: 100%;
		background: #F6F6F6;
		scrollIndicator: 'none';
	}


	::-webkit-scrollbar {
		width: 0;
		height: 0;
		background-color: transparent;
	}
</style>
