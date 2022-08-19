<template>
	<view class="content">
		<view class="header">
			<view class="l font-weight-bold">
				我的
			</view>
			<view class="r rounded-bottom-lg ">
				<image src="../../static/demo/my/更多.png" class="px-2 py-1"></image>
			</view>
		</view>
		<my-dl></my-dl>
		<my-dh :list='list'></my-dh>
		<my-cd :lists='lists'></my-cd>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: [{
						url: '../../static/demo/my/订单.png',
						title: '订单'
					},
					{
						url: '../../static/demo/my/消息.png',
						title: '消息'
					},
					{
						url: '../../static/demo/my/收藏.png',
						title: '收藏'
					},
					{
						url: '../../static/demo/my/自学习工具.png',
						title: '在学'
					}
				],
				lists: [{
						icon: '../../static/demo/my/优惠券.png',
						name: '我的优惠券',
						rightArrow: '../../static/demo/my/右箭头.png'
					},
					{
						icon: '../../static/demo/my/常见问题／相关问题.png',
						name: '常见问题',
						rightArrow: '../../static/demo/my/右箭头.png'
					},
					{
						icon: '../../static/demo/my/设置.png',
						name: '设置',
						rightArrow: '../../static/demo/my/右箭头.png'
					},
				]
			}
		},
		methods: {

		}
	}
</script>

<style>
	.header {
		height: 80rpx;
		background-color: #5ccc84;
		display: flex;
		border-bottom: none;
	}

	.l {
		flex: 1;
		line-height: 80rpx;
		text-align: center;
		color: #fff;
	}

	.r image {
		width: 70rpx;
		height: 70rpx;
	}
</style>
