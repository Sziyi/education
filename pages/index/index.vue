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
		
		<i-icon-nav></i-icon-nav>
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
				}]
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>

</style>
