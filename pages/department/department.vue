<template>
	<view class="container">
		<view class="content-top">
			<view class="content-topbox1">
				<icon class="iconfont iconsousuo" />
				<icon class="iconfont iconsaoyisao" />
				<icon class="iconfont iconqingchu" @click="empty" v-show="searchdata" />
				<input class="uni-input" confirm-type="search" v-model="searchdata" placeholder-style="color: #FFFFFF;"  placeholder="器具编号" />
			</view>
		</view>
		<view class="content-cen">
			<view class="listing">
				<view class="listing-title">待送样清单 <text>同单器具</text></view>
				<scroll-view v-if="radioItems.length>0" :scroll-top="scrollTop" scroll-y="true" class="scroll-Y"  @scrolltoupper="upper" @scrolltolower="lower" @scroll="scroll">
					<checkbox-group @change="checkboxChange" class="uni-list">
						<view class="checkbox-list" v-for="(item,index) in radioItems" :key="index">
							<checkbox class="uni-listbox1" style="transform:scale(0.8)" :value="item.value" :checked="item.checked" />
							<view class="uni-listbox2" @click="todetails">
								<view class="uni-listname uni-listnum"><text>委托编号：</text>1234567891</view>
								<view class="uni-listname"><text>客服：</text>刘伟</view>
								<view class="uni-listname"><text>委托日期：</text>2020-01-15</view>
								<view class="uni-listname"><text>单位名称：</text>深圳市中图仪器股份有限公司</view>
								<view class="uni-listname"><text>检后服务：</text>器具优先送返</view>
							</view>
						</view>
					</checkbox-group>
				</scroll-view>
				<view class="empty" v-else>
					<image src="../../static/img/logo.png" mode=""></image>
					<view class="">暂无内容，请先检索</view>
				</view>
			</view>
			<view class="inspection">
				<view class="listing-title">送检详情</view>
				<view class="inspection-cen">
					<view class="inspection-cenlist">
						<text>经办人</text>
						<input class="uni-input" placeholder-style="color:#BFBFBF" placeholder="请输入" />
					</view>
					<view class="inspection-cenlist timeoperation">
						<text>操作时间</text>
						<e-picker-plus @confirm="confirm" :style="time=='点击选择'?'color:#BFBFBF':'color:#595959'">{{time}}</e-picker-plus>
						<icon class="iconfont iconjiantou" />
					</view>
					<view class="inspection-cenlist">
						<text>备注</text>
						<input class="uni-input" placeholder-style="color:#BFBFBF" placeholder="请输入" />
					</view>
				</view>
			</view>
		</view>
	    <view class="content-footer">
	    	 <button class="remove" plain="true" hover-class="removehover" type="primary">移除</button>
			 <button class="into"  plain="true" hover-class="intohover"  type="primary">送入</button>
	    </view>
	</view>
</template>

<script>
	import epickerplus from '@/components/e-picker-plus/e-picker-plus';
export default {
	components: {
		epickerplus
	},
	data() {
		return {
			searchdata:'',
			scrollTop: 0,
			time:'点击选择',
			radioItems: [
				// {
				// 	name: 'USA',
				// 	value: '美国',
				// },
				// {
				// 	name: 'CHN',
				// 	value: '中国',
				// },
				// {
				// 	name: 'HG',
				// 	value: '韩国',
				// },
				// {
				// 	name: 'DG',
				// 	value: '德国',
				// },
				// {
				// 	name: 'FG',
				// 	value: '法国',
				// },
				// {
				// 	name: 'YG',
				// 	value: '英国',
				// },
				// {
				// 	name: 'RB',
				// 	value: '日本',
				// }
			],
		};
	},
	methods: {
		confirm(e) {
			console.log(e)
			this.time=e.result
		},
		empty(){
			this.searchdata=''
		},
		choose(e){
			
		},
		checkboxChange (e){
			console.log(e.target.value)
		},
		todetails(){
			uni.navigateTo({
			    url: '/pages/utensil/utensil'
			});
		},
		upper: function(e) {
			// console.log(e)
		},
		lower: function(e) {
			// console.log(e)
		},
		scroll: function(e) {
			// console.log(e)
			// this.old.scrollTop = e.detail.scrollTop
		},
	}
};
</script>

<style lang="scss" scoped>
.container {
	.content-top{
		background-color: #75C23A;
		padding: 20rpx 40rpx;
		position: relative;
		text{
			position: absolute;
			top:0rpx;
			right: 0rpx;
			font-weight: 600;
			line-height: 6vh;
			color: #262626;
		}
		.content-topbox1 {
			position: relative;
			background-color: rgba(255, 255, 255, 0.16);
			border-radius: 36rpx;
			.iconsousuo,.iconsaoyisao,.iconqingchu {
				position: absolute;
				color: #FFFFFF;
				top:0rpx;
			}
			.iconsousuo {
				left: 20rpx;
				line-height: 72rpx;
			}
			.iconsaoyisao {
				right: 20rpx;
				font-weight: 600;
				line-height: 72rpx;
			}
			.iconqingchu{
				right: 80rpx; 
				font-weight: 600;
				line-height: 72rpx;
			}
			.uni-input {
				width: calc(100% - 190rpx);
				padding-left: 70rpx;
				height: 72rpx;
				font-size: 28rpx;
				line-height: 72rpx;
				color: #FFFFFF;
			}
		}
	}
	.content-cen{
		margin: 20rpx 40rpx 40rpx;
		width: calc(100% - 80rpx);
		.listing{
			min-height: 336rpx;
			background: #FFFFFF;
			box-shadow: 0px 12rpx 28rpx rgba(0, 0, 0, 0.08);
			border-radius: 12rpx;
			font-size: 28rpx;
			color: #404040;
			.listing-title{
				padding: 20rpx;
				text{
					float: right;
					color: #75C23A;
				}
			}
			.scroll-Y{
				width: calc(100% - 20rpx);
				padding: 0 20rpx;
				max-height: 704rpx; 
				.checkbox-list{
					margin-top: 20rpx;
					position: relative;
					padding-left: 30rpx;
			        border-bottom: 1px solid #E6E6E6;
					.uni-listbox1{
						position: absolute;
						right: 20rpx;
						top: 0rpx;
					}
					.uni-listbox2{
						.uni-listname{
							height: 60rpx;
							line-height: 60rpx;
						}
					}
				}
			}
		    .empty{
				text-align: center;
				image{
					margin-top: 20rpx;
					width: 112rpx;
					height: 112rpx;
				}
				view{
					margin-top: 20rpx;
					font-size: 28rpx;
					font-weight: 400;
					color: #404040;
				}
			}
		}
		.inspection{
			margin-top: 20rpx;
			height: 380rpx;
			background: #FFFFFF;
			box-shadow: 0px 12rpx 28rpx rgba(0, 0, 0, 0.08);
			border-radius: 12rpx;
			font-size: 28rpx;
			color: #404040;
			.listing-title{
				padding: 20rpx;
				text{
					float: right;
					color: #75C23A;
				}
			}
			.inspection-cen{
				padding: 0 20rpx ;
				.inspection-cenlist{
					overflow: hidden;
					font-size: 32rpx;
					height: 100rpx;
					line-height: 100rpx;
                    border-bottom: 1px solid #E6E6E6;
					text{
						display: inline-block;
						width: 30%;
						float: left;
						color: #8C8C8C;
					}
					.uni-input{
						height: 100rpx;
						line-height: 100rpx;
						width: 70%;
						float: left;
						color: #595959;
					}
					
				}
				.inspection-cenlist:nth-child(3){
					border-bottom: 0px solid #E6E6E6;
				}
				.timeoperation{
					position: relative;
					.iconjiantou{
						position: absolute;
						top: 0rpx;
						right: 0rpx;
						color: #BFBFBF;
						font-size: 28rpx;
					}
				}
			}
		}
	}
	.content-footer{
		position: fixed;
		bottom: 20rpx;
		width: 100%;
		// padding: 0 5%;
		text-align: center;
		button{
			width: 40%;
			margin: 0 10rpx;
			height: 80rpx;
			line-height: 80rpx;
			font-size: 36rpx;
			border-radius: 8rpx;
			display: inline-block;
			border: 0px solid #FF656D;
		}
		.remove{
			background: rgba(230, 230, 230, 1);
			color: #FF656D;
		}
		.removehover{
			background: rgba(230, 230, 230, .49);
			color: #F7959B;
		}
		.into{
			background: rgba(117, 194, 58, 1);
			color: #FFFFFF;
		}
		.intohover{
			background:rgba(117, 194, 58, .49);
		}
	}
}
</style>
