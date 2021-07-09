<template>
	<view>
		首页
	</view>
</template>

<script>
	export default {
		data() {
			return {
				swipers:[]
			}
		},
		onLoad() {
			this.getSwipers()
		},
		methods: {
			// 获取轮播图数据
			getSwipers(){
				uni.request({
					url:"https://api-hmugo-web.itheima.net/api/public/v1/home/swiperdata",
					success:function(res){
						console.log(res)
						 
					}
				})
			}
		}
	}
</script>
