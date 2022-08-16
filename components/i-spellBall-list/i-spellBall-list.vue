<template>
	<view class="sp">
		<scroll-view scroll-x="true" class="scroll-row">
			<view v-for="i in spellBall" :key="i" class="coupon fl bo">
				<view>
					<image :src="i.cover" class="img"></image>
					<view class="box">
						<text v-html="i.type=='media'?'图文':''" class="tw"></text>
						<text v-html="i.type=='column'?'专栏':''" class="tw"></text>
						<text v-html="i.type=='video'?'视频':''" class="tw"></text>
							<text v-html="i.type=='audio'?'音频':''" class="tw"></text>
					</view>
					<view class="tit px-2">
						<text class="ti">{{i.title}}</text>
					</view>
					<text class="price px-2">￥{{i.price}}</text>
					<text class="t_price">￥{{i.t_price}}</text>
				</view>

			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		name: 'i-spellBall-list',
		props: ['spellBall'],
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
		height: 290rpx;
		/* background-color: #007AFF; */
		border-bottom: 15rpx solid #efefef;
	}

	.img {
		width: 340rpx;
		height: 200rpx;
		display: flex;

	}

	.bo {
		position: relative;

	}

	.coupon {
		width: 340rpx;
		display: inline-flex;
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

	.tit {
		width: 340rpx;
		box-sizing: border-box;
		overflow: hidden;
		white-space: nowrap;
		text-overflow: ellipsis;
	}
</style>
