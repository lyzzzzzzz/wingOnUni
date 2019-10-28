<template>
	<view class="content">
		<view id="img"></view>
		<view style="width: 100%;flex: 1;">
			<view style="margin-top: 20rpx;width: 100%;" class="flex">
				<uni-segmented-control :current="current" :values="items" @clickItem="onClickItem" style-type="button" active-color="#217ABF"
				 style="height: 70rpx;width: 90%;font-weight: bold;"></uni-segmented-control>
				<view style="width: 90%;display: flex;margin-top: 40rpx;" class="flex">
					<view style="width: 100%;">
						<text class="text">Country code:</text>
						<view class="uni-list">
							<view class="uni-list-cell" style="width: 100%;">
								<view class="uni-list-cell-db flex" style="width: 100%;">
									<view style="display: flex;flex-direction: row;justify-content: space-between;align-items: center;width:100%;height: 70rpx;border: 1px solid  #C8C7CC;flex: 1;margin-top: 5px;">
										<input class="uni-input" style="height: 70rpx;padding-left: 10px;width: 100%;" :value="array[index]" />
										<picker @change="bindPickerChange" :value="index" :range="array" style="background: #C8C7CC;width: 50px;text-align: center;height: 70rpx;">
											▼
										</picker>
									</view>
								</view>
							</view>
						</view>
					</view>

					<view style="width: 100%;margin-top: 40rpx;">
						<text class="text">Phone Number:</text>
						<input class="uni-input" style="border: 1px solid  #C8C7CC;height: 70rpx;padding-left: 10px;margin-top: 10rpx;"
						 v-model="tel" />
					</view>
				</view>

				<view class="content" style="width: 100%;">
					<view v-show="current === 0" style="width: 100%;">
						<view style="width: 90%;margin: auto;">
							<view style="display: flex;flex-direction: row;justify-content: space-between;align-items: center;margin-top: 40rpx;">
								<view><text class="text">OPT verify code:</text></view>
								<view><button style="font-size: 24rpx;background: #E41F30;color: #FFFFFF;line-height: 50rpx;" :disabled="optDisabled"
									 @tap="sendOpt">{{countdown}}</button></view>
							</view>
							<input class="uni-input" style="border: 1px solid  #C8C7CC;height: 70rpx;padding-left: 10px;margin-top: 10rpx;" />
						</view>
					</view>

					<view v-show="current === 1" style="width: 100%;margin-top: 40rpx;">
						<view style="width: 90%;margin: auto;">
							<text class="text">Password:</text>
							<input class="uni-input" style="border: 1px solid  #C8C7CC;height: 70rpx;padding-left: 10px;margin-top: 10rpx;"
							 v-model="password" />
						</view>
					</view>
				</view>




				<view style="width: 100%;margin-top: 60rpx;" @tap="toHome">
					<button style="width: 90%;background: #E41F30;color: #FFFFFF;font-weight: bold;font-size: 40rpx;line-height: 80rpx;">Login</button>
				</view>



				<view style="width: 90%;margin-top: 60rpx;display: flex;flex-direction: row;justify-content: space-between;align-items: center;font-size: 24rpx;">
					<text style="text-decoration: underline;">Forget Password</text>
					<text style="text-decoration: underline;">No Account? Join Us Now!</text>
				</view>

			</view>

		</view>
	</view>
</template>

<script>
	import uniSegmentedControl from "@/components/uni-segmented-control/uni-segmented-control.vue"
	import environment from '../../common/js/environment.js'
	export default {
		components: {
			uniSegmentedControl
		},
		data() {
			return {
				items: ['SMS Login', 'Password Login'],
				current: 0,
				title: 'picker',
				array: [],
				index: 0,
				language: '',
				tel: '',
				code: '',
				telCountryCode: [],
				countdown: 'Send OPT',
				time: 60,
				optDisabled: false,
				password: ''
			}
		},
		methods: {
			onClickItem(index) {
				if (this.current !== index) {
					this.current = index;
				}
			},
			bindPickerChange: function(e) {
				this.index = e.target.value
			},
			toHome: function() {
				if (this.current == 0) {
					this.loginWithSms()
				} else if (this.current == 1) {
					this.loginWithPwd()
				}
			},
			loginWithSms: function() {

				uni.navigateTo({
					url: '../home/index'
				});


			},
			loginWithPwd: function() {
			uni.navigateTo({
				url: '../home/index'
			});
			


				var telCountryCode = this.telCountryCode[this.index].code




  // const phone = uni.getSystemInfoSync();
		// 		uni.request({
		// 			url: environment.baseUrl + 'security/login/' + telCountryCode + "/" + this.tel + "/" + this.password,
		// 			method: 'POST',
		// 			data: {},
		// 			dataType: 'json',
		// 			header: {
		// 				'Accept-Language': 'en',
		// 				'deviceOS': phone.platform,
		// 			},
		// 			success: res => {
		// 				if(res.code==200){
		// 				console.log(res.data)					
		// 				}
		
		// 			},
		// 			fail: () => {},
		// 			complete: () => {}
		// 		});

			},
			setTime: function() {
				console.log('loginWithPwd')
			},

			sendOpt: function() {
				var _this = this
				if (!_this.array[_this.index]) {
					uni.showToast({
						title: 'telCountryCode is empty!',
						duration: 2000,
						icon: 'none',
						position: 'bottom'
					});
					return false;
				}

				if (!_this.tel) {
					uni.showToast({
						title: 'Phone Number is empty!',
						duration: 2000,
						icon: 'none',
						position: 'bottom'
					});
					return false;
				}

				var code = _this.telCountryCode[_this.index].code //获取country code

				if (_this.time == 60) {
					_this.optDisabled = true
					_this.countdown = "wait..." + _this.time + "s...";
					_this.time--;
					setTimeout(function() {
						_this.sendOpt()
					}, 1000)

				} else if (_this.time == 0) {
					_this.optDisabled = false
					_this.countdown = "Send OTP Again";
					_this.time = 60;
				} else {
					_this.optDisabled = true
					_this.countdown = "wait..." + _this.time + "s...";
					_this.time--;
					setTimeout(function() {
						_this.sendOpt()
					}, 1000)
				}





			},


		},
		onLoad: function() {
			var _this = this;
			uni.getStorage({
				key: 'language',
				success: function(res) {
					uni.request({
						url: environment.baseUrl + 'config/list/telCountryCode/all',
						method: 'GET',
						data: {},
						header: {
							'Accept-Language': res.data
						},
						success: function(response) {
							var telCountryCode = response.data.data.telCountryCode
							var code = ''
							var name = ''
							var text = ''
							var list = []
							_this.telCountryCode = telCountryCode
							for (var i = 0; i < telCountryCode.length; i++) {
								code = telCountryCode[i].code
								name = telCountryCode[i].name
								text = '+' + code + ' ' + name

								list.push(text)
							}
							_this.array = list

						},
						fail: () => {
							console.log('请求telCountryCode错误')
						},
						complete: () => {}
					});

				},
				fail: function() {
					console.log('获取language错误')
				}
			});



		}
	}
</script>

<style>
	page {
		width: 100%;
		height: 100%;
	}

	.content {
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	#img {
		width: 100%;
		height: 300rpx;
		background-image: url('https://raw.githubusercontent.com/lyzzzzzzz/img/master/image_login.png');
		background-repeat: no-repeat;
		background-size: cover;
	}

	.btn {
		width: 50%;
		height: 35px;
		padding: 0px;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: center;
	}

	.flex {
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		align-items: center;
	}

	.text {
		font-size: 32rpx;
	}

	button::after {
		border: none;
	}
</style>
