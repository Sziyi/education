<template>
	<view>
	<view class="dh shadow">
		<view class="img" v-for="i in list" :key='i'>
			<image :src="i.url" mode=""></image>
			<text class="font-sm pt-1">{{i.title}}</text>
		</view>
	</view>
	</view>
</template>

<script>
	export default {
		name:'my-dh',
		props:['list'],
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	.dh{
		width: 92%;
		height: 180rpx;
		background-color: #fff;
		position: absolute;
		top: 350rpx;
		left: 4%;
		border-radius: 20rpx;
		display: flex;
		justify-content: space-around;
	}
	
.img{
	width: 70rpx;
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
}
.img image{
	width: 50rpx;
	height: 50rpx;
}
</style>
