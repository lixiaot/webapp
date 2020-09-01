<template>
	<view class="container">
		<view class="content-top">
			<view class="content-topbox1">
				<icon class="iconfont iconsousuo" />
				<icon class="iconfont iconsaoyisao" />
				<icon class="iconfont iconqingchu" @click="empty" v-show="searchdata" />
				<input class="uni-input" confirm-type="search" v-model="searchdata"  placeholder="搜索你想要的..." />
			</view>
			<text>搜索</text>
		</view>
		<view class="content-cen">
			<view class="cen-lists">
				<view class="cen-list-top">
					办理状态
				</view>
				<view class="cen-list-cen">
					<text @click="choose('待入库')" class="cen-list-itme">待入库</text>
					<text @click="choose('待收入')" class="cen-list-itme">待送人</text>
					<text @click="choose('待会去')" class="cen-list-itme">待取回</text>
					<text @click="choose('待出库')" class="cen-list-itme">待出库</text>
					<text @click="choose('待出库')" class="cen-list-itme">已出库</text>
				</view>
			</view>
			<view class="cen-lists">
				<view class="cen-list-top">
					业务分类
				</view>
				<view class="cen-list-cen">
					<text class="cen-list-itme">委托出库</text>
					<text class="cen-list-itme">下厂返厂</text>
					<text class="cen-list-itme">本地送检</text>
					<text class="cen-list-itme">下厂取件</text>
				</view>
			</view>
			<view class="cen-lists">
				<view class="cen-list-top">
					主检科室
				</view>
				<view class="cen-list-cen">
					<text class="cen-list-itme">电学</text>
					<text class="cen-list-itme">力学</text>
					<text class="cen-list-itme">长度</text>
					<text class="cen-list-itme">热工</text>
					<text class="cen-list-itme">理化</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			searchdata:''
		};
	},
	methods: {
		empty(){
			this.searchdata=''
		},
		choose(e){
			
		}
	}
};
</script>

<style lang="scss" scoped>
.container {
	.content-top{
		margin: 0rpx 40rpx;
		position: relative;
		text{
			position: absolute;
			top:0rpx;
			right: 0rpx;
			font-weight: 600;
			line-height: 5vh;
			color: #262626;
		}
		.content-topbox1 {
			width: calc(100% - 90rpx);
			padding: 0 40prx;
			position: relative;
			background-color: #F5F5F5;
			border-radius: 36rpx;
			.iconsousuo,.iconsaoyisao,.iconqingchu {
				position: absolute;
				color: #979797;
				top:0rpx;
			}
			.iconsousuo {
				left: 20rpx;
				line-height: 5vh;
			}
			.iconsaoyisao {
				right: 20rpx;
				font-weight: 600;
				line-height: 5vh;
			}
			.iconqingchu{
				right: 80rpx; 
				font-weight: 600;
				line-height: 5vh;
			}
			.uni-input {
				width: calc(100% - 190rpx);
				padding-left: 70rpx;
				height: 5vh;
				line-height: 5vh;
				color: #262626;
			}
		}
	}
	.content-cen{
		margin:40rpx;
		color: #404040;
		.cen-lists{
			margin-top: 20rpx;
			.cen-list-top{
				font-weight: 600;
				font-size: 32rpx;
			}
			.cen-list-cen{
				margin-top: 20rpx;
				.cen-list-itme{
					display: inline-block;
					font-size: 28rpx;
					padding: 14rpx;
					margin-left: 20rpx;
					margin-bottom: 20rpx;
					background:rgba(245,245,245,1);
					border-radius:8rpx; 
				}
				.cen-list-itme:hover{
				    color: #FFFFFF; 
					background:#75C23A;
				}
			}
		}
	}
}
</style>
