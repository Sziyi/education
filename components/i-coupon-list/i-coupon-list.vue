<template>
	<view class="p-2">
		<scroll-view scroll-x="true" class="scroll-row">
			<view v-for="i in list" :key="i" class="coupon">
				<view>
					<text>￥{{i.price}}</text>
					<text class="font">
					<text class="font1" v-html="i.type=='column'?'适用专栏':'适用课程'"></text>：{{i.value.title}}</text>
				</view>
				<view hover-class="bg-hover-warning">
					领取
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		name: "coupon-list",
		props:['list'],
		data() {
			return {
				
			};
		},
		onLoad() {

		},
		methods: {}
	}
</script>

<style>
	.coupon {
		width: 500rpx;
		display: inline-flex;
		color: #ffffff;
		margin-right: 30rpx;
	}

	.coupon>view:first-child {
		padding: 20rpx 30rpx;
		background-color: #d39e00;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		border-right: 4rpx dashed;
	}

	.coupon>view:last-child {
		width: 120rpx;
		display: flex;
		align-items: center;
		justify-content: center;
		background-color: #ffc107;
		font-size: 30rpx !important;
	}
	.font1{
		font-size: 20rpx;
	}
</style>
