<template>
	<view class="home">
		<swiper indicator-dots circular autoplay>
			<swiper-item v-for="item in swipers" :key='item.goods_id'>
				<image :src="item.image_src"></image>
			</swiper-item>
		</swiper>

		<!-- 导航区域 -->
		<view class="nav">
			<view class="nav_item">
				<view class="iconfont icon-index-fill"></view>
				<text>河马超市</text>
			</view>
			<view class="nav_item">
				<view class="iconfont icon-icon_zhanghao"></view>
				<text>联系我们</text>
			</view>
			<view class="nav_item">
				<view class="iconfont icon-index-fill"></view>
				<text>我的社区</text>
			</view>
			<view class="nav_item">
				<view class="iconfont icon-icon_zhanghao"></view>
				<text>好好学习</text>
			</view>
		</view>
		
		<!-- 推荐商品区 -->
		<view class="hot_goods">
			<view class="tit">推荐商品</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				swipers: []
			}
		},
		onLoad() {
			this.getSwipers()
		},
		methods: {
			// 获取轮播图数据
			async getSwipers() {
				// uni.request({
				// 	url:"https://api-hmugo-web.itheima.net/api/public/v1/home/swiperdata",
				// 	data:"",
				// 	success:res=>{
				// 		console.log(res) 
				// 		if(res.data.meta.status !== 200) {
				// 			return uni.showToast({
				// 				title:'获取数据失败'
				// 			})
				// 		}
				// 		this.swipers = res.data.message
				// 	}
				// })

				const res = await this.$myRequest({
					url: '/api/public/v1/home/swiperdata'
				})
				console.log(res)
				this.swipers = res.data.message
			}
		}
	}
</script>

<style lang="scss">
	.home {
		swiper {
			width: 750rpx;
			height: 380rpx;

			image {
				width: 100%;
				height: 100%;
			}
		}
	}
	
	.nav{
		display: flex;
		.nav_item{
			width: 25%;
			text-align: center;
			margin-top: 10rpx;
			view{
				width: 120rpx;
				height: 120rpx;
				background: $shop-color;
				border-radius: 60rpx;
				margin: 10rpx auto;
				line-height: 120rpx;
				color: #fff;
				font-size: 60rpx;
			}
			text{
				font-size: 30rpx;
			}
		}
	}
	
	.hot_goods{
		background: #eee;
		overflow: hidden;
		margin-top: 10rpx;
		.tit{
			height: 100rpx;
			line-height: 100rpx;
			color: $shop-color;
			text-align: center;
			margin: 7rpx 0;
			background: #fff;
			letter-spacing: 20rpx;
		}
	}
</style>
