<template>
	<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000" style="height: 310rpx;">
		<swiper-item class="flex justify-center" v-for="(item,index) in data" :key="index">
			<image :src="item.src"  style="width: 720rpx;height: 300rpx;" class="rounded shadow">
			</image>
		</swiper-item>
	</swiper>
</template>

<script>
	export default {
		name: 'i-swiper',
		props: {
			data: {
				type: Array,
				default: () => []
			}
		},
		data() {
			return {

			}
		},
		methods: {
			toDetail(item) {
				this.$emit("click", item)
			}
		}
	}
</script>

<style>

</style>
