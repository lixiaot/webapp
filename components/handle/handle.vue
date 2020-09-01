<template>
	<view class="handle">
		<view class="handle-list" :style="status==1?'color: #262626;':''">
			<icon class="iconfont iconshoufaruku" />
			<text>收发入库</text>
		</view>
		<view class="handle-list" @click="print" :style="status==2?'color: #262626;':''">
			<icon class="iconfont iconsongrukeshi" />
			<text>送入科室</text>
		</view>
		<view class="handle-list" :style="status==3?'color: #262626;':''">
			<icon class="iconfont iconfanhuishoufa" />
			<text>返回收货</text>
		</view>
		<view class="handle-list" :style="status==2||status==4?'color: #262626;':''">
			<icon class="iconfont iconchuku" />
			<text>收发出库</text>
		</view>
		<view class="handle-list" @click="print"  :style="status==5?'color: #262626;':''">
			<icon class="iconfont icondayin" />
			<text>打印标签</text>
		</view>
		<uni-popup id="dialogInput" ref="dialogInput" type="dialog">
			<uni-popup-dia :type="msgType" title="通知" content="欢迎使用 uni-popup!" :before-close="true" @confirm="dialogConfirm" @close="dialogClose"></uni-popup-dia>
		</uni-popup>
	</view>
</template>

<script>
	import uniPopup from "@/components/uni-popup/uni-popup.vue";
	import uniPopupDia from '@/components/uni-popup/uni-popup-dia.vue'
	export default {
		components: {
			uniPopup,
			uniPopupDia
		},
		props:{
			status: {
				type: Number,
				default: 1
			},
		},
		data() {
			return {
				msgType: 'success',
			};
		},
		onLoad() {},
		onReady() {},
		onShow() {},
		onHide() {},
		methods: {
			todepartment(){
				uni.navigateTo({
				    url: '/pages/utensil/utensil'
				});
			},
			print(){
				if(this.status==5){
					this.$refs.dialogInput.open()
				}else if(this.status==2){
					uni.navigateTo({
					    url: '/pages/department/department'
					});
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
	.handle{
		position: fixed;
		display: flex;
		bottom: 0;
		width: 100%;
		background-color: #FFFFFF;
		box-shadow:0px 2px 6px rgba(0,11,22,0.3);
		height: 140rpx;
		.handle-list{
			flex: 1;
			color: #999999;
			text-align: center;
			margin: 14rpx 0;
			.iconfont{
				font-size: 44rpx;
			}
			text{
				margin-top: 14rpx;
				display: block;
				font-size: 28rpx;
			}
		}
	}
</style>
