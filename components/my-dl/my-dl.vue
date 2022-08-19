<template>
	<view>
		<view class="two">
			<view class="dl">
				<view class="tx bg-hover-light mt-5 ml-2"></view>
				<view class="login pt-5 pl-3">
					<text @click="login">立即登录</text>
					<text class="font-sm pt-3">登录解锁更多功能</text>
				</view>
			</view>
		</view>

	</view>
</template>

<script>
	export default {
		name: 'my-dl',
		data() {
			return {

			}
		},
		methods: {
			login(){
				uni.navigateTo({
					url:'../../pages/login/login'
				})
			}
		}
	}
</script>

<style>
	.two {
		height: 450rpx;
		background-color: #5ccc84;
		margin-top: -2rpx;
		border-bottom-left-radius: 30%;
		border-bottom-right-radius: 30%;
		position: relative;
	}

	.dl {
		display: flex;
		color: #fff;
	}

	.tx {
		width: 120rpx;
		height: 120rpx;
		border-radius: 50%;
	}

	.login {
		display: flex;
		flex-direction: column;
	}
</style>
