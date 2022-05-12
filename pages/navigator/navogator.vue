<template>
	<view>

		<navigator url="/pages/detail/detail?id=80&age=19">跳转至详情页</navigator>
		<!-- 关闭当前页面，跳转到应用内的某个页面 -->
		<navigator url="/pages/detail/detail" open-type="redirect">跳转到详情页并关闭当前页面</navigator>
		
		
		
		<view> --------------  </view>
		<button @click="goDetail">跳转之详情页</button>
		<button type="primary" @click="redirectDetail()">跳转到详情页并关闭当前页面</button>
		
		
		<view> --------------  </view>
		<!-- <button type="primary" @click="addToCar">加入购物车</button> -->
	<navigator url="/pages/contact/contact" open-type="switchTab">跳转至联系我们</navigator>

	</view>
</template>

<script>
	export default {
		onUnload() {
			console.log('导航页面卸载了')
		},
		
		methods: {
			goDetail () {
				uni.navigateTo({
					url: '/pages/detail/detail?id=80&age=19'
				})
			},
		
			redirectDetail () {
				uni.redirectTo({
					url: '/pages/detail/detail'
				});
			},
			addToCar () {
				uni.$emit('updateCart',{
					id: 10,
					name: '贸易'
				})
			}
		}
	}
</script>

<style>
</style>
