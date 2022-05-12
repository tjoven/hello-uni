<template>
	<view class="content">
		<!-- 自定义子组件test -->
		<!-- <test v-if="flag" :title="title" @myEven="getNum"></test> -->
			<!-- 这是子组件传递过来的数据{{num}} -->
<!-- 			<test-a></test-a>
			<test-b></test-b> -->
			<!-- <uni-calendar
				:insert="true"
				:lunar="true" 
				:start-date="'2021-3-2'"
				:end-date="'2022-5-20'"
				@change="change"
				 > 
				 	</uni-calendar>-->
			
		<!-- 输入框 -->
		<input type="text"  value="输入框默认值" @input="input"  />
			
		<!-- hidden 属性值是变量 -->
		<!-- title 内容值是变量 -->
		<text :hidden = "flag" >Text组件显示{{title}}</text>
		
		<!-- 点击事件 -->
		<button type="primary" @click="checkTest">Text组件隐藏{{flag}}</button>
	
		<!-- 页面跳转 -->
		<button type="primary" @click="navogator">页面跳转到 导航</button>
		<button type="primary" @click="navogator_list">页面跳转到 列表</button>
	
	</view>
</template>

<script>
	import test from '../../components/test.vue'
	import testA from '../../components/a.vue'
	import testB from '../../components/b.vue'
	import uniCalendar from '@/components/uni-calendar/uni-calendar.vue'
	export default {
		data() {
			return {
				title: 'Hello',
				num: 0,
				flag: true
			}
		},
		onLoad(options) {
			console.log('页面加载了',options)
		},
		onShow() {
			console.log('页面显示了')
		},
		onReady(){
			console.log('页面初次渲染完成了')
		},
		onHide() {
			console.log('页面隐藏了')
		},
		methods: {
			checkTest () {
				this.flag = !this.flag
			},
			getNum (num) {
				console.log(num)
				this.num = num
			},
			input(e) {
				console.log('输入',e.detail)
			},
			navogator(){
				uni.navigateTo({
					// 路径 已"/"开头
					// url: "/pages/navigator/navogator",
						url: "../navigator/navogator",
					success() {
						console.log('navigateTo','success')
					},
					fail(e) {
						console.log(e)
					}
				})
			},
			navogator_list(){
				uni.navigateTo({
						url: "/pages/list/list"
				})
			}
		},
		components: {
			test,
			"test-a": testA,
			"test-b": testB,
			uniCalendar
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
