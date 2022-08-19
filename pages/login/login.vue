<template>
	<view class="content">
		<view class="top">
			<image src="../../static/demo/login/左箭头.png" class="p-2" @click="fh"></image>
		</view>
		<view class="dl">
			<h2 v-show='!retrieve'>{{flag?'登 录':'注册'}}</h2>
			<h2 v-show='retrieve'>找回密码</h2>
			<view class="input" v-show="!retrieve">
				<image src="../../static/demo/login/用户.png" mode=""></image>
				<!-- <uni-icons type="person"></uni-icons> -->
				<input type="text" v-model="form.username" placeholder="请输入用户名" />
			</view>
			<view class="input" v-show="retrieve">
				<image src="../../static/demo/login/用户.png" mode=""></image>
				<input type="text" v-model="form.phone" placeholder="请输入手机号" />
			</view>
			<view class="input" v-show="retrieve">
				<image src="../../static/demo/login/密码锁定.png" mode=""></image>
				<input type="text" v-model="form.code" placeholder="验证码" />
				<view class="yzm" type="default">发送</view>
			</view>
			<view class="input">
				<image src="../../static/demo/login/密码锁定.png" mode=""></image>
				<input type="password" v-model="form.password" placeholder="请输入密码" />
			</view>
			<view class="input" v-show="!flag">
				<image src="../../static/demo/login/密码锁定.png" mode=""></image>
				<input type="password" v-model="form.repassword" placeholder="请输入确认密码" />
			</view>
			<button type="default" @click="handleSubmitForm" v-show="!retrieve">{{flag?'登录':'注册'}}</button>
			<button type="default" v-show="retrieve">立即找回</button>
			<view class="zc">
				<text class="zczh" @click="zc" v-show='!retrieve'>{{flag?'注册账号':'去登录'}}</text>
				<text class="wjPassword" v-show="!retrieve" @click="zh">忘记密码</text>
			</view>
			<view class="icon" v-show="!retrieve">
				<image src="../../static/demo/login/微信.png" mode=""></image>
			</view>
			<view class="read mt-4" v-show="flag">
				<checkbox-group @change="handleCheckboxStatus">
					<label class="text-light-muted">
						<checkbox :checked="check" color="#7fd49e" style="transform: scale(0.7);" /><text
							class="font">已阅读并同意用户协议&隐私声明</text>
					</label>
				</checkbox-group>

			</view>
		</view>
	</view>
</template>

<script>
	import UserModel from "@/model/userModel"
	export default {
		data() {
			return {
				flag: true, //登录、注册
				retrieve: false, //忘记密码
				check: false, //单选框
				form: { //input框
					username: '',
					phone: '',
					code: '',
					password: '',
					repassword: ''
				},

			}
		},
		methods: {
			// 点击返回按钮
			fh() {
				// if (this.flag === true) {
				// 	uni.switchTab({
				// 		url: "../my/my"
				// 	})
				// } else {
				uni.navigateBack({
					delta: 1
				})
				// }
			},
			handleSubmitForm() {
				uni.showLoading({
					title: '提交中...',
					mask: false
				})
				 !this.flag ? this.handleRegisterAccont() : this.handleLoginAccont()
			},
			// 登录、注册
			zc() {
				this.flag = !this.flag
			},
			/**
			 * 注册
			 */
			async handleRegisterAccont() {
				try {
					const data = this.loadsh.cloneDeep(this.form)
					const response = await UserModel.userRegister(data)
					uni.showToast({
						title: '注册成功',
						icon: 'none'
					})
					this.flag=true
					this.resetForm()
				} catch (err) {
					console.log(err)
				} finally {
					uni.hideLoading()
				}
			},
			/**
			 * 登录
			 */
			async handleLoginAccont() {
				if (!this.check) {
					return uni.showToast({
						title: '请先阅读并同意用户协议&隐私声明',
						icon: "none"
					})
				}
				try {
					const data = this.loadsh.cloneDeep(this.form)
					delete data.repassword
					delete data.code
					delete data.phone
					const response = await UserModel.userLogin(data)
					console.log('data',data)
					this.resetForm()
					this.$store.dispatch("setUser", response)

					this.handleToBindPhonePage()

					uni.navigateBack({
						delta: -1
					})
				} catch (err) {
					console.log(err)
				} finally {
					uni.hideLoading()
				}
			},
			/**
			 * 如果用户登录之后,没有绑定手机号,则跳转到绑定手机号的页面
			 */
			handleToBindPhonePage() {
				const user = this.$store.state.user
				console.log(user)
				if (!user.phone) {
					// 跳转到绑定手机号的页面
					setTimeout(() => {
						uni.redirectTo({
							url: "/pages/bind-phone/bind-phone"
						})
					}, 350)
					// 并且不再继续往下执行
					return
				}
			},
			// 获取checkbox状态
			handleCheckboxStatus(event) {
				this.check = Boolean(event.detail.value.length)
				// console.log(this.check)
			},
			// 清空表单
			resetForm() {
				this.form = {
					username: '',
					password: '',
					repassword: ''
				}
			},
			// 找回密码
			zh() {
				this.retrieve = !this.retrieve
			},
		}
	}
</script>

<style>
	.content {
		height: 100vh;
		background-image: linear-gradient(to right, #86f3ba, #8fd4f1);
	}

	.top image {
		width: 60rpx;
		height: 60rpx;
	}

	.dl {
		width: 100%;
		height: 88%;
		background-color: #fff;
		position: absolute;
		bottom: 0;
		border-top-left-radius: 4%;
		border-top-right-radius: 4%;
	}

	.dl h2 {
		margin: 70rpx 80rpx;
	}

	.input {
		width: 80%;
		height: 110rpx;
		background-color: #f5f5f5;
		display: flex;
		align-items: center;
		margin-left: 10%;
		margin-top: 40rpx;
		border-radius: 10rpx;
	}

	button {
		width: 80%;
		height: 100rpx;
		margin-top: 40rpx;
		background-color: #5ccc84;
		color: #fff;
	}

	.dl image {
		width: 40rpx;
		height: 40rpx;
	}

	.zc {
		width: 80%;
		height: 140rpx;
		line-height: 140rpx;
		display: flex;
		justify-content: space-between;
		margin-left: 10%;
	}

	.zczh {
		color: #5ccc84;
	}

	.wjPassword {
		color: #ccc;

	}

	.icon {
		width: 100%;
		display: flex;
		justify-content: center;
	}

	.icon image {
		width: 120rpx;
		height: 120rpx;
	}

	.read {
		width: 80%;
		margin-left: 10%;
		color: #ccc;
	}

	.yzm {
		width: 202rpx;
		height: 100%;
		text-align: center;
		line-height: 110rpx;
		margin-top: 0;
		margin-right: 0;
		background-color: #5CCC84;
		color: #fff;
		border-top-right-radius: 10rpx;
		border-bottom-right-radius: 10rpx;
	}
</style>
