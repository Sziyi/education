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
					iconNav:[{
									src:"/static/demo/icon/hd.png",
									name:"活动",
								},{ 
									src:"/static/demo/icon/test.png",
									name:"考试",
								},{
									src:"/static/demo/icon/ms.png",
									name:"秒杀",
								},{
									src:"/static/demo/icon/pt.png",
									name:"拼团",
								},{
									src:"/static/demo/icon/course.png",
									name:"直播",
								},{
									src:"/static/demo/icon/column.png",
									name:"专栏",
								},{
									src:"/static/demo/icon/book.png",
									name:"电子书",
								},{
									src:"/static/demo/icon/ask.png",
									name:"社区",
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
