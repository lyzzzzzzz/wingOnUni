<template>
	<view>
		<scroll-view>
			<view v-for="item in list" :key="item.id">
				<view>
					<view style="width: 100%;height: 300rpx;;" class="img">

					</view>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: [{

				}]
			}
		},
	}
</script>

<style>
	page {
		width: 100%;
	}

	.img {
		background-image: url('~@/static/message/inbox_banner.png');
		background-repeat: no-repeat;
		background-size: cover;
	}
</style>
