<template>
		<view class="uni-list">
			<view class="uni-list-cell" hover-class="uni-list-cell-hover" v-for="(item,index) in list" :key="index" @click="info(item.post_id )" >
				<view class="uni-media-list">
					<image class="uni-media-list-logo" :src="item.author_avatar"></image>
					<view class="uni-media-list-body">
						<view class="uni-media-list-text-top">{{item.title}}</view>
						<view class="uni-media-list-text-bottom uni-ellipsis">{{item.created_at }}</view>
					</view>
				</view>
			</view>
		</view>
</template>

<script>
	export default {
		data() {
			return {
				list:""
			}
		},
		onLoad() {
			uni.request({
				url: 'https://unidemo.dcloud.net.cn/api/news',
				method: 'GET',
				data: {},
				success: res => {
					console.log(res)
					this.list=res.data
				},
				fail: () => {},
				complete: () => {}
			});
		},
		methods: {
			info(id){
				console.log(id)
				uni.navigateTo({
					url: '../info/info?id='+id,
					success: res => {},
					fail: () => {},
					complete: () => {}
				});
			}
		}
	}
</script>

<style>
	.uni-media-list{
		width: 100%;
		display: flex;
		
	}
	.uni-media-list-body{
		width: 96%;
		padding:10rpx 2%;
		height: 100rpx;
	}
</style>

