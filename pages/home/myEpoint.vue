<template>
	<view class="content">

		<view class="qiun-charts3">
			<!--#ifdef MP-ALIPAY -->
			<canvas canvas-id="canvasArcbar3" id="canvasArcbar3" class="charts3" :style="{'width':cWidth3*pixelRatio+'px','height':cHeight3*pixelRatio+'px', 'transform': 'scale('+(1/pixelRatio)+')','margin-left':cWidth3*2-cWidth3*(pixelRatio-1)/2+'px','margin-top':-cHeight3*(pixelRatio-1)/2+'px'}"></canvas>
			<!--#endif-->
			<!--#ifndef MP-ALIPAY -->
			<canvas canvas-id="canvasArcbar3" id="canvasArcbar3" class="charts3"></canvas>
			<!--#endif-->
		</view>
		<text style="font-size: 32rpx;">Last Updated at 11/10/2019 08:09:05</text>


		<view class="list">

			<uni-list style="width: 100%;">
				<uni-list-item title="标题文字"></uni-list-item>
				<uni-list-item title="标题文字" class="item"></uni-list-item>
			</uni-list>

		</view>
	

	</view>
</template>

<script>
	import uCharts from '../../components/u-charts/u-charts.js';
	import uniList from "@/components/uni-list/uni-list.vue"
	import uniListItem from "@/components/uni-list-item/uni-list-item.vue"
	var _self;

	export default {
		components: {
			uniList,
			uniListItem
		},

		data() {
			return {
				cWidth3: '', //圆弧进度图
				cHeight3: '', //圆弧进度图
				arcbarWidth: '', //圆弧进度图，进度条宽度,此设置可使各端宽度一致
				pixelRatio: 1,
			}
		},
		onLoad() {
			_self = this;
			//#ifdef MP-ALIPAY
			uni.getSystemInfo({
				success: function(res) {
					if (res.pixelRatio > 1) {
						//正常这里给2就行，如果pixelRatio=3性能会降低一点
						//_self.pixelRatio =res.pixelRatio;
						_self.pixelRatio = 2;
					}
				}
			});
			//#endif

			this.cWidth3 = uni.upx2px(450);
			this.cHeight3 = uni.upx2px(450);
			this.arcbarWidth = uni.upx2px(34);
		},
		onReady() {
			this.fillData();
		},
		methods: {

			fillData() {
				var epoint = 2500
				let Arcbar3 = {
					series: [{
						name: '/5,000 epoint',
						data: epoint / 5000,
						color: '#E41F30',
						epoint: epoint
					}]
				};

				this.showArcbar3("canvasArcbar3", Arcbar3);
			},

			showArcbar3(canvasId, chartData) {
				new uCharts({
					$this: _self,
					canvasId: canvasId,
					type: 'arcbar',
					fontSize: 11,
					title: {
						name: Math.round(chartData.series[0].epoint),
						// name: Math.round(1000),
						color: chartData.series[0].color,
						fontSize: 25 * _self.pixelRatio
					},
					subtitle: {
						name: chartData.series[0].name,
						color: '#666666',
						fontSize: 16 * _self.pixelRatio,
						offsetX: 17,
						offsetY: 10
					},
					extra: {
						arcbar: {
							type: 'circle', //整圆类型进度条图
							width: _self.arcbarWidth * _self.pixelRatio, //圆弧的宽度
							startAngle: 0.5 //整圆类型只需配置起始角度即可
						}
					},
					background: '#FFFFFF',
					pixelRatio: _self.pixelRatio,
					series: chartData.series,
					animation: true,
					width: _self.cWidth3 * _self.pixelRatio,
					height: _self.cHeight3 * _self.pixelRatio,
					dataLabel: true,
				});
			},
		}
	}
</script>

<style>
	page,
	.content {
		background: #FFFFFF;
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
		align-items: center;
	}


	/* 圆弧进度样式 */
	.qiun-charts3 {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 60%;
		width: 100%;
	}

	.charts3 {
		width: 450upx;
		height: 450upx;
		text-align: center;
	}

	.list {
		width: 100%;
		bottom: 0px;
		/* position: absolute; */
	}

	
</style>
