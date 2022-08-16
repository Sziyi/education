<template>
	<view class="content">
		<view class="header">
			<view class="l">
				我的
			</view>
			<view class="r">
				<image src="../../static/demo/my/更多.png" class="px-2 py-1"></image>
			</view>
		</view>
		<view class="two">
			
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>
.header{
	height: 80rpx;
	background-color: #5ccc84;
	display: flex;
	border-bottom:none;
}
.l{
	width: 85%;
	line-height: 80rpx;
	text-align: center;
	color: #fff;
}
.r image{
	width: 70rpx;
	height: 70rpx;
}
.two{
	height: 465rpx;
	background-color: #5ccc84;
	margin-top: -2rpx;
}
</style>
