<template>
	<view class="content">
		<!-- 搜索框 -->
		<i-search-bar></i-search-bar>
		<!-- 轮播图 -->
		<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000" style="height: 310rpx;">
			<swiper-item class="flex justify-center" v-for="(item,index) in swiper" :key="index">
				<image :src="item.src" mode="aspectFill" style="width: 720rpx;height: 300rpx;" class="rounded shadow">
				</image>
			</swiper-item>
		</swiper>
		<!-- 导航 -->
		<i-icon-nav :list='iconNav'></i-icon-nav>
		<!-- 优惠券 -->
		<i-coupon-list :list='list'></i-coupon-list>
		<!-- 拼团 -->
		<view class="pt px-2">
			<b>拼团</b>
		</view>
		<i-spellBall-list :spellBall="spellBall"></i-spellBall-list>
		<!-- 最新列表 -->
		<view class="list px-2">
			<b>最新列表</b>
			<text class="r">查看更多</text>
		</view>
		<i-latest-list :latest='lat'></i-latest-list>
		<!-- 底部 -->
		<view class="fotter">
			<image src="../../static/demo/cover/1.png" mode=""></image>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				swiper: [{
					src: "/static/demo/banner/banner1.png"
				}, {
					src: "/static/demo/banner/banner2.png"
				}],
				iconNav: [{
					src: "/static/demo/icon/hd.png",
					name: "活动",
				}, {
					src: "/static/demo/icon/test.png",
					name: "考试",
				}, {
					src: "/static/demo/icon/ms.png",
					name: "秒杀",
				}, {
					src: "/static/demo/icon/pt.png",
					name: "拼团",
				}, {
					src: "/static/demo/icon/course.png",
					name: "直播",
				}, {
					src: "/static/demo/icon/column.png",
					name: "专栏",
				}, {
					src: "/static/demo/icon/book.png",
					name: "电子书",
				}, {
					src: "/static/demo/icon/ask.png",
					name: "社区",
				}],
				list: [],
				spellBall: [],
				latest: [],
				lat:[]
			}

		},
		onLoad() {
			this.List()
			this.spellBallList()
			this.latestList()
		},
		methods: {
			List() {
				uni.request({
					url: 'http://demonuxtapi.dishait.cn/mobile/coupon',
					method: "GET",
					header: {
						appid: 'bd9d01ecc75dbbaaefce'
					},
					success: (res) => {
						this.list = res.data.data
						console.log('res', res)
					},
					fail: (err) => {
						console.log(err)
					}
				})
			},
			spellBallList() {
				uni.request({
					url: 'http://demonuxtapi.dishait.cn/mobile/group',
					method: "GET",
					header: {
						appid: 'bd9d01ecc75dbbaaefce'						
					},
					data:{
						usable: 1,
						page: 1
					},
					success: (res) => {
						this.spellBall = res.data.data.rows
						console.log('res', res.data.data.rows)
					},
					fail: (err) => {
						console.log(err)
					}
				})
			},
			latestList() {
				uni.request({
					url: 'http://demonuxtapi.dishait.cn/mobile/group',
					method: "GET",
					header: {
						appid: 'bd9d01ecc75dbbaaefce'
					},
					data:{
						page: 1,
						usable: 1,
					},
					success: (res) => {
						this.latest = res.data.data.rows
						this.lat=this.latest.splice(3)
						console.log('lat', this.lat)
						console.log('res', res.data.data.rows)
					},
					fail: (err) => {
						console.log(err)
					}
				})
			}
		}
	}
</script>

<style>
	.pt {
		height: 100rpx;
		line-height: 100rpx;
		font-size: 40rpx;
		border-top: 15rpx solid #efefef;
	}

	.list {
		height: 100rpx;
		line-height: 100rpx;
		display: flex;
		justify-content: space-between;
	}

	.r {
		font-size: 26rpx;
		color: #ccc;
	}
	.fotter{
		width: 100%;
		height:350rpx;
		
	}
	.fotter image{
		width: 100%;
		height: 340rpx;
	}
</style>
