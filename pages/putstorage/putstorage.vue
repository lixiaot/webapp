<template>
	<view class="content">
		<view class="content-top" style="background-image: url(http://chuantu.xyz/t6/740/1598837387x977013264.png);background-size: cover">
			<view class="content-topbox1">
				<icon class="iconfont iconsousuo" />
				<icon class="iconfont iconsaoyisao" @click="toscanCode" />
				<!-- <input class="uni-input" confirm-type="search" placeholder-style="color: #FFFFFF;" placeholder="搜索" /> -->
				<view class="uni-input" @click="topage">搜索</view>
			</view>
			<view class="content-topbox2">
				<view class="topbox2-date" :style="date ? 'background-color: #FFFFFF;' : 'background-color: rgba(255, 255, 255, 0.16);'" @click.stop="open">
					<icon class="iconfont iconrili" :style="date ? 'color: #CCCCCC;' : ''" />
					<text :style="date ? 'color: #404040;' : ''">{{ date ? date : '选择日期' }}</text>
					<icon v-if="date" class="iconfont iconqingchu" @click.stop="qingchu" />
					<icon v-else class="iconfont iconjiantou" />
				</view>
				<view :class="datetwo?'topbox2-day topbox2-day2':'topbox2-day'" @click="choosedate">最近两天</view>
				<view class="topbox2-note">注：最近两天下厂 日期的最后两天</view>
			</view>
			<view class="content-topbox3">
				<view :class="flag==1?'active':'current'" @click="switchlist(1)"><text>20</text>待入库</view>
				<view :class="flag==2?'active':'current'" @click="switchlist(2)"><text>45</text>待送样</view>
				<view :class="flag==3?'active':'current'" @click="switchlist(3)"><text>125</text>待取回</view>
				<view :class="flag==4?'active':'current'" @click="switchlist(4)"><text>17</text>待入库</view>
				<view :class="flag==5?'active':'current'" @click="switchlist(5)">已出库</view>
			</view>
		</view>
		<view class="content-cen">
			<scroll-view :scroll-top="scrollTop" scroll-y="true" class="scroll-Y"  @scrolltoupper="upper" @scrolltolower="lower" @scroll="scroll">
				<checkbox-group @change="checkboxChange" class="uni-list">
					<view class="checkbox-list" v-for="(item,index) in radioItems" :key="index">
						<label class="uni-list-cell uni-list-cell-pd"  >
							<checkbox class="uni-listbox1" style="transform:scale(0.8)" :value="item.value" :checked="item.checked" />
						</label>
						<view class="uni-listbox2" @click="todetails">
							<view class="uni-listname">
								广州市中图有限公司{{index}}
							</view>
							<view class="uni-listdepartment">部门：企划部</view>
						</view>
						<view class="uni-listtyle">72H</view>
					</view>
				</checkbox-group>
			</scroll-view>
		</view>
		<view class="datekuang"><calendar :lunar="false" :insert="false" :range="false" ref="calendar" :disable-before="true" :showMonth="false" @close="close" @change="change" /></view>
		<handle :status="flag"></handle>
	</view>
</template>
<script>
import calendar from '@/components/uni-calendar/uni-calendar';
import handle from '@/components/handle/handle';
export default {
	components: {
		calendar,
		handle
	},
	data() {
		return {
			flag:1,
			date: '',
			datetwo:false,
			scrollTop: 0,
			Height:'',
			radioItems: [{
			                    name: 'USA',
			                    value: '美国',
			                },
			                {
			                    name: 'CHN',
			                    value: '中国',
			                },
							{
			                    name: 'HG',
			                    value: '韩国',
			                },
							{
							    name: 'DG',
							    value: '德国',
							},
							{
							    name: 'FG',
							    value: '法国',
							},
							{
							    name: 'YG',
							    value: '英国',
							},
							{
							    name: 'RB',
							    value: '日本',
							}
			            ],
		};
	},
	onLoad() {},
	onReady() {},
	onShow() {},
	onHide() {},
	methods: {
		toscanCode(){
			// 允许从相机和相册扫码
			uni.scanCode({
			    success: function (res) {
			        console.log('条码类型：' + res.scanType);
			        console.log('条码内容：' + res.result);
			    }
			});
		},
		choosedate(){
			this.datetwo=!this.datetwo
		},
		checkboxChange (e){
			console.log(e.target.value)
		},
		switchlist(e){
			this.flag=e;
		}, 
		topage(){
			uni.navigateTo({
			    url: '/pages/search/search'
			});
		},
		todetails(){
			uni.navigateTo({
			    url: '/pages/details/details'
			});
		},
		open() {
			uni.hideTabBar()
			this.$refs.calendar.open(); 
		},
		change(e) {
			this.date = e.fulldate;
			uni.showTabBar()
		},
		qingchu() {
			this.date = '';
			uni.showTabBar()
		},
		close(){
			uni.showTabBar()
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
.content {
	font-size: 28rpx;
	.datekuang {
		padding: 20rpx;
	}
	.content-top {
		position: relative;
		height: 30vh;
		padding: 1vh 40rpx;
		.content-topbox1 {
			.iconsousuo,
			.iconsaoyisao {
				position: absolute;
				color: #ffffff;
			}
			.iconsousuo {
				left: 60rpx;
				line-height: 5vh;
			}
			.iconsaoyisao {
				right: 80rpx;
				font-weight: 600;
				line-height: 5vh;
			}
			.uni-input {
				width: calc(100% - 80rpx);
				padding-left: 70rpx;
				height: 5vh;
				line-height: 5vh;
				background-color: rgba(255, 255, 255, 0.16);
				border-radius: 36rpx;
				color: #ffffff;
			}
		}
		.content-topbox2 {
			overflow: hidden;
			margin-top: 2vh;
			.topbox2-date {
				height: 6vh;
				float: left;
				line-height: 6vh;
				background-color: rgba(255, 255, 255, 0.16);
				width: 296rpx;
				border-radius: 8rpx;
				color: #ffffff;

				.iconrili {
					padding: 0 2vh;
				}
				.iconjiantou,
				.iconqingchu {
					float: right;
					margin-right: 20rpx;
					font-size: 24rpx;
				}
				.iconqingchu {
					color: #cccccc;
				}
			}
			.topbox2-day {
				float: left;
				margin-left: 20rpx;
				height: 6vh;
				line-height: 6vh;
				text-align: center;
				background-color: rgba(255, 255, 255, 0.16);
				width: 172rpx;
				border-radius: 8rpx;
				color: #ffffff;
			}
				
			.topbox2-day2{
				background-color: #FFFFFF;
				color: #404040;
			}
			.topbox2-note {
				float: right;
				padding-top: 1vh;
				width: 160rpx;
				height: 6vh;
				font-size: 20rpx;
				font-family: PingFang SC;
				font-weight: bold;
				line-height: 24rpx;
				color: rgba(250, 250, 250, 1);
				opacity: 0.6;
			}
		}
		.content-topbox3 {
			margin-top: 1vh;
			display: -webkit-box;
			display: -webkit-flex;
			display: -ms-flexbox;
			display: flex;
			-webkit-box-pack: justify;
			-webkit-justify-content: space-between;
			-ms-flex-pack: justify;
			justify-content: space-between;
			view {
				width: 8vh;
				display: block;
				height: 8vh;
				background: rgba(255, 255, 255, 0.23);
				border-radius: 8rpx;
				text-decoration: none;
				text-align: center;
				color: #ffffff;
				font-size: 28rpx;
				text {
					display: block;
					margin-top: 1.5vh;
				}
			}
			view:nth-child(5) {
				line-height: 8vh;
			}
			.active{
				position: relative;
				background: #FFFFFF;
				color: #A7A7A7;
				text {
					color: #404040;
				}
			}
			.current:after{
				width: 0;
			}
			.active:after{
				content: '';
				width: 30%;
				height: 4rpx;
				background-color: #FFFFFF;
				border-radius: 2rpx;
				position: absolute;
				left: 50%;
				bottom: -20rpx;
				-webkit-transform: translateX(-50%);
				transform: translateX(-50%);
				-webkit-transition: .3s;
				transition: .3s;  
			}
		}
	}
    .content-cen{
		position: fixed;
		top: 28vh;
		width: calc(100% - 40rpx);
		padding: 0 20rpx;
		.scroll-Y {
			height:  60vh;
			.uni-list{
				text-align: center;
				.checkbox-list{
					position: relative;
					text-align: left;
					width: calc(100% - 80rpx);
					display: inline-block;
					margin-bottom: 20rpx;
					height: 160rpx;
					line-height: 160rpx;
					padding: 0 24rpx;
					background:rgba(255,255,255,1);
					border-radius: 20rpx;
					box-shadow:0px 12rpx 18rpx rgba(0,0,0,0.08);
					overflow: hidden;
					.uni-list-cell{
						.uni-listbox1{
							float: left;
						}
					}
					.uni-listbox2{
						line-height: 60rpx;
						margin-top: 20rpx;
						margin-left: 20rpx;
						float: left;
						display: block;
						.uni-listname{
							font-size: 32rpx;
							font-weight: 600;
							color: #404040;
						}
						.uni-listdepartment{
							font-size: 28rpx;
							color: #8C8C8C;
						}
					}
					.uni-listtyle{
						position: absolute;
						top: 20rpx;
						font-size: 28rpx;
						right: 24rpx;
						background:rgba(255,101,109,1);
						width: 96rpx;
						height: 48rpx;
						line-height: 48rpx;
						border-radius: 24rpx;
						color: #FFFFFF;
						text-align: center;
					}
									
				}
				
			}
		}
	}
}
</style>
