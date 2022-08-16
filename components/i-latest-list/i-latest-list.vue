<template>
	<view class="sp">
		<scroll-view class="scroll-row">
			<view v-for="i in latest" :key="i" class="coupon fl px-2  py-2 bo">
				<view>
					<view class="nn">
						<image :src="i.cover" class="img"></image>
						<view class="box">
							<text v-html="i.type=='media'?'图文':''" class="tw"></text>
							<text v-html="i.type=='column'?'专栏':''" class="tw"></text>
							<text v-html="i.type=='video'?'视频':''" class="tw"></text>
							<text v-html="i.type=='audio'?'音频':''" class="tw"></text>
						</view>
						<view class="tit px-2">
							<view class="ti">
								<text>{{i.title}}</text>
							</view>
							<view class="price">
								<text class="price">￥{{i.price}}</text>
								<text class="t_price">￥{{i.t_price}}</text>
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="coupon fl px-2  py-2 bo">
				<view>
					<view class="nn">
						<image src="../../static/demo/cover/1.png" class="img"></image>
						<view class="box">
							<text class="tw">图文</text>
						</view>
						<view class="tit px-2">
							<view class="ti">
								<text>uni-app实战视频点播app小程序</text>
							</view>
							<view class="price">
								<text class="price">￥9.98</text>
								<text class="t_price">￥20.00</text>
							</view>
						</view>
					</view>
				</view>
			
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		name: 'i-latest-list',
		props: ['latest'],
		data() {
			return {

			}
		},
		methods: {

		}
	}
</script>

<style>
	.sp {
		/* background-color: #007AFF; */
		border-bottom: 15rpx solid #efefef;
	}

	.img {
		width: 340rpx;
		height: 200rpx;
	}

	.bo {
		position: relative;
		display: flex;
	}

	.coupon {
		width: 340rpx;
	}

	.nn {
		display: flex;
	}

	.tit {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}
.ti{
	width: 340rpx;
	box-sizing: border-box;
	overflow: hidden;
	white-space: nowrap;
	text-overflow: ellipsis;
}
	.coupon>view:first-child {
		flex-direction: column;
	}

	.box {
		width: 60rpx;
		height: 40rpx;
		background-color: rgba(0, 0, 0, .2);
		position: absolute;
		top: 160rpx;
		left: 278rpx;
	}

	.tw {
		font-size: 24rpx;
		color: #fff;
		line-height: 40rpx;
		text-align: center;
	}

	.price {
		font-size: 32rpx;
		color: red;
	}

	.t_price {
		font-size: 24rpx;
		color: grey;
	}
</style>
