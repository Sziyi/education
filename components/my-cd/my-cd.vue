<template>
	<view>
		<view class="cd mt-4">
			<view class="single pl-2" v-for="ite in lists" :key='ite'>
				<view class="le">
					<image :src="ite.icon" mode=""></image>
					<text class="name pl-1">{{ite.name}}</text>
				</view>
				<view class="ri">
					<image :src="ite.rightArrow" mode=""></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:'my-cd',
		props:['lists'],
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>
.cd{
	height: 500rpx;
}
.single{
	height: 130rpx;
	border-bottom:2rpx solid #ccc ;
	display: flex;
	justify-content: space-between;
}
.le{
		display: flex;
}
.ri{
	width: 10%;
}
.single image{
	width: 50rpx;
	height: 50rpx;
	margin-top: 40rpx;	
}
.name{
	line-height: 130rpx;
}
</style>
