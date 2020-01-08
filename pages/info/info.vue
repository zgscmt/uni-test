<template>
	<view class="content">
		<view class="con-title">{{title}}</view>
		<view class="con-tontent"><rich-text class="richText" :nodes="strings"></rich-text></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title:"",
				strings:""
			}
		},
		onLoad:function(e){
			console.log(e)
			uni.request({
				url: 'https://unidemo.dcloud.net.cn/api/news/36kr/'+e.id,
				method: 'GET',
				data: {},
				success: res => {
					this.title=res.data.title;
					this.strings=res.data.content;
				},
				fail: () => {},
				complete: () => {}
			});
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
