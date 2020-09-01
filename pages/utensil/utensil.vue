<template>
	<view class="container">
		<view class="head">
		   <view class="head-left"><image src="../../static/img/head-left.png" mode=""></image></view>  感应静电仪{{a==1?'<':''}}电学{{a==1?'>':''}} <view class="head-right"><image src="../../static/img/head-left.png" mode=""></image></view>
		</view>
		<view style="height: 100%;">
			<view class="tabs">
			    <scroll-view id="tab-bar" class="scroll-h" :scroll-x="true" :show-scrollbar="false" :scroll-into-view="scrollInto">
			        <view v-for="(tab,index) in tabBars" :key="tab.id" class="uni-tab-item" :id="tab.id" :data-current="index" @click="ontabtap">
			            <text class="uni-tab-item-title" :class="tabIndex==index ? 'uni-tab-item-title-active' : ''">{{tab.name}}</text>
						<text :class="tabIndex==index ? 'bian' : ''"></text>
			        </view>
			    </scroll-view>
			    <!-- <view class="line-h"></view> -->
			    <swiper  :current="tabIndex" class="swiper-box" style="flex: 1;" :duration="300" @change="ontabchange">
			        <swiper-item class="swiper-item" v-for="(tab,index1) in newsList" :key="index1">
						<!-- #ifndef APP-NVUE -->
						<scroll-view class="scroll-v list" enableBackToTop="true" scroll-y >
							<view class="list1" v-if="index1==0">
								<view class="list1-li">
									<text>办理状态</text>已归还
								</view>
								<view class="list1-li">
									<text>最后所在位置</text>收发
								</view>
								<view class="list1-li">
									<text>当前持有人</text>卫东
								</view>
								<view class="list1-li">
									<text>器具状态</text>正常
								</view>
								<view class="list1-li">
									<text>入库人</text>鹿野
								</view>
								<view class="list1-li">
									<text>入库时间</text>2020-04-17 10:25:56
								</view>
								<view class="list1-li">
									<text>出库人</text>张氏
								</view>
								<view class="list1-li">
									<text>出库时间</text>2020-04-17 10:25:56
								</view>
								<view class="list1-li">
									<text>操作人</text>/
								</view>
								<view class="list1-li">
									<text>出库时间</text>2020-04-17 10:25:56
								</view>
								<view class="list1-li">
									<text>业务类型</text>下厂送返
								</view>
								
								<view class="list1-li">
									<text>存放位置</text>快递放置区
								</view>
								<view class="list1-li">
									<text>快递放置区</text>/
								</view>
								<view class="list1-li">
									<text>商定完成日期</text>2020-04-05
								</view>
							</view>
						    <view class="listbox"  v-if="index1==1">
								<view class="list2">
									<view class="list2-li1">
										<text>器具编号</text>K234567890
									</view>
									<view class="list2-li1">
										<text>出厂编号</text>GD9T00001
									</view>
									<view class="list2-li1">
										<text>仪器设备别名</text>表面静电测试仪
									</view>
									<view class="list2-li1">
										<text>管理编号</text>/
									</view>
									<view class="list2-li1">
										<text>型号规格</text>慧测FMX-003（国产）
									</view>
									<view class="list2-li1">
										<text>入库时间</text>2020-04-17 10:25:56
									</view>
								</view>
								<view class="list3">
									<view class="list2-li1">
										<text>主检科室</text>K234567890
									</view>
									<view class="list2-li1">
										<text>单位</text>GD9T00001
									</view>
									<view class="list2-li1">
										<text>仪器设备分类</text>表面静电测试仪
									</view>
									<view class="list2-li1">
										<text>电源电压</text>/
									</view>
									<view class="list2-li1">
										<text>对接客服</text>慧测FMX-003（国产）
									</view>
									<view class="list2-li1">
										<text>业务类型</text>2020-04-17 10:25:56
									</view>
									<view class="list2-li1">
										<text>加急要求</text>K234567890
									</view>
									<view class="list2-li1">
										<text>器具来源</text>GD9T00001
									</view>
									<view class="list2-li1">
										<text>器具创建人</text>表面静电测试仪
									</view>
									<view class="list2-li1">
										<text>器具创建时间</text>/
									</view>
									<view class="list2-li1">
										<text>加急要求</text>慧测FMX-003（国产）
									</view>
									<view class="list2-li1">
										<text>外观说明</text>2020-04-17 10:25:56
									</view>
									<view class="list2-li1">
										<text>特殊要求</text>慧测FMX-003（国产）
									</view>
									<view class="list2-li1">
										<text>器具备注</text>/
									</view>
								</view>
						    </view>
							<view class="list1" v-if="index1==2">
								<view class="list1-li">
									<text>委托单位名称</text>委托单位名称
								</view>
								<view class="list1-li dizhi" >
									<text class="wizhi">委托单位地址</text><text class="dibox">深圳市龙华区大浪街道新石 社区丽荣路1号昌毅工业厂 区2号一层</text>
								</view>
								<view class="list1-li">
									<text>联系部门</text>资源库房管理部
								</view>
								<view class="list1-li">
									<text>固定电话</text>(0755)81726870
								</view>
								<view class="list1-li">
									<text>分机号</text>8382
								</view>
								<view class="list1-li">
									<text>客户联系人</text>李晓华
								</view>
								<view class="list1-li">
									<text>联系人手机</text>1542662365
								</view>
								<view class="list1-li">
									<text>联系人手机2</text>1542662365
								</view>
								<view class="list1-li">
									<text>E-mail</text>xhli@ipi-tech.com
								</view>
								<view class="list1-li">
									<text>委外处理</text>同意
								</view>
								<view class="list1-li">
									<text>任务进度</text>委托单管理
								</view>
								<view class="list1-li">
									<text>合同编号</text>PC123456788
								</view>
								<view class="list1-li">
									<text>委托日期</text>2020-02-02 15:52:26
								</view>
								<view class="list1-li">
									<text>客户类型</text>VIP
								</view>
								<view class="list1-li">
									<text>业务员</text>张广龙
								</view>
								<view class="list1-li">
									<text>检后服务</text>自取 异常器具处理、超差出证书
								</view>
							</view>
						    <view class="listbox"  v-if="index1==3">
						    	<view class="listfujian">
						    		<view class="listfujian-top">
										<view>备注</view>
										<textarea class="listfujian-textarea" placeholder-style="color:#8C8C8C" placeholder="首次测试实验报告"/>
									</view>
									<view class="listfujian-cen">
										<text>实验室测试成功报告</text>
										<text>报告来源于青之实验室</text>
										<text>实验室不能操作，转外处理，需要三天</text>
									</view>
									<view class="listfujian-img" >
										<view>图片(选填)</view>
										<view class="uni-uploader-body" >
											<view class="uni-uploader__files" >
												<block v-for="(image,index) in imageList" :key="index">
													<view class="uni-uploader__file">
														<image class="uni-uploader__img" :src="image" :data-src="image" @tap="previewImage"></image>
														<icon class="iconfont iconqingchu" />
													</view>
												</block>
												<view class="uni-uploader__input-box">
													<view class="uni-uploader__input"  @tap="chooseImage">
														<icon class="iconfont icontianjia" />
														<text>添加图片</text>
													</view>
												</view>
											</view>
										</view>
									</view>
						    	    <view class="uni-btn-v">
						    	    	<button form-type="submit">保存</button>
						    	    </view>
								</view>
						        <view class="listfiles">
									<view class="">
										全部文件
									</view>
									<view class="listf">
										<view class="listfi">
											20190808-青之-报告证书实例.pdf<icon class="iconfont iconxiazai"  @click="Download" />
										</view>
										<view class="listfi">
											20190808-青之-报告证书实例.pdf<icon class="iconfont iconxiazai"  @click="Download" />
										</view>
										<view class="listfi">
											20190808-青之-报告证书实例.pdf<icon class="iconfont iconxiazai"  @click="Download" />
										</view>
									</view>
								</view>
							</view>
						</scroll-view>
						<!-- #endif -->
			        </swiper-item>
			    </swiper>
			</view>
		</view>
		<handle :status="flag"></handle>
	</view>
</template>

<script>
var sourceType = [
	['camera'],
	['album'],
	['camera', 'album']
]
var sizeType = [
	['compressed'],
	['original'],
	['compressed', 'original']
]
import handle from '@/components/handle/handle'; 
import uniPopup from "@/components/uni-popup/uni-popup.vue";
import uniPopupDialog from '@/components/uni-popup/uni-popup-dialog.vue'
export default {
	components: {
		handle,
		uniPopup,
		uniPopupDialog
	},
	data() {
		return {
			flag:2,
			a:1,
			imageList: [],
			title: 'choose/previewImage',
			imageList: [],
			sourceTypeIndex: 2,
			sourceType: ['拍照', '相册', '拍照或相册'],
			sizeTypeIndex: 2,
			sizeType: ['压缩', '原图', '压缩或原图'],
			countIndex: 8,
			count: [1, 2, 3, 4, 5, 6, 7, 8, 9],
			newsList: [1,2,3,4],
			cacheTab: [],
			tabIndex: 0,
			tabBars: [{
				name: '收发信息',
				id: 'guanzhu'
			}, {
				name: '仪器/设备详情',
				id: 'tuijian'
			}, {
				name: '委托详情',
				id: 'tiyu'
			}, {
				name: '收发附件',
				id: 'redian'
			}],
			scrollInto: "",
			showTips: false,
			navigateFlag: false,
			pulling: false,
		};
	},
	onLoad() {
	    
	},
	methods: {
		previewImage: function(e) {
			var current = e.target.dataset.src
			uni.previewImage({
				current: current,
				urls: this.imageList
			})
		},
		chooseImage: async function() {
			// #ifdef APP-PLUS
			// TODO 选择相机或相册时 需要弹出actionsheet，目前无法获得是相机还是相册，在失败回调中处理
			if (this.sourceTypeIndex !== 2) {
				let status = await this.checkPermission();
				if (status !== 1) {
					return;
				}
			}
			// #endif
		
			if (this.imageList.length === 9) {
				let isContinue = await this.isFullImg();
				console.log("是否继续?", isContinue);
				if (!isContinue) {
					return;
				}
			}
			uni.chooseImage({
				sourceType: sourceType[this.sourceTypeIndex],
				sizeType: sizeType[this.sizeTypeIndex],
				count: this.imageList.length + this.count[this.countIndex] > 9 ? 9 - this.imageList.length : this.count[this.countIndex],
				success: (res) => {
					this.imageList = this.imageList.concat(res.tempFilePaths);
				},
				fail: (err) => {
					// #ifdef APP-PLUS
					if (err['code'] && err.code !== 0 && this.sourceTypeIndex === 2) {
						this.checkPermission(err.code);
					}
					// #endif
					// #ifdef MP
					uni.getSetting({
						success: (res) => {
							let authStatus = false;
							switch (this.sourceTypeIndex) {
								case 0:
									authStatus = res.authSetting['scope.camera'];
									break;
								case 1:
									authStatus = res.authSetting['scope.album'];
									break;
								case 2:
									authStatus = res.authSetting['scope.album'] && res.authSetting['scope.camera'];
									break;
								default:
									break;
							}
							if (!authStatus) {
								uni.showModal({
									title: '授权失败',
									content: 'Hello uni-app需要从您的相机或相册获取图片，请在设置界面打开相关权限',
									success: (res) => {
										if (res.confirm) {
											uni.openSetting()
										}
									}
								})
							}
						}
					})
					// #endif
				}
			})
		},
	    ontabtap(e) {
	        let index = e.target.dataset.current || e.currentTarget.dataset.current;
	        this.switchTab(index);
	    },
	    ontabchange(e) {
	        let index = e.target.current || e.detail.current;
	        this.switchTab(index);
	    },
	    switchTab(index) {
			console.log(index)
	        if (this.tabIndex === index) {
	            return;
	        }
	        this.tabIndex = index;
	        this.scrollInto = this.tabBars[index].id;
	        
	    },
		Download() {
			uni.downloadFile({
				url: 'http://192.168.0.200:8058/files/200200711.doc',//下载地址接口返回
				success: (data) => {
					if (data.statusCode === 200) {
						//文件保存到本地
						uni.saveFile({
							tempFilePath: data.tempFilePath, //临时路径
							success: function(res) {
								uni.showToast({
									icon: 'none',
									mask: true,
									title: '文件已保存：' + res.savedFilePath, //保存路径
									duration: 3000,
								});
								setTimeout(() => {
									//打开文档查看
									uni.openDocument({
										filePath: res.savedFilePath,
										success: function(res) {
											// console.log('打开文档成功');
										}
									});
								}, 3000)
							}
						});
					}
				},
				fail: (err) => {
					console.log(err);
					uni.showToast({
						icon: 'none',
						mask: true,
						title: '失败请重新下载',
					});
				},
			});
		},
	}
};
</script>

<style lang="scss" scoped>
.container {
	height: 100%;
	.head {
		height:8vh;
		line-height: 8vh;
		text-align: center;
	    color: #FFFFFF;
		background:rgba(131,195,83,1);
		position: relative;
		.head-left,.head-right{
			position: absolute;
			top: 30rpx;
			width: 48rpx;
			height: 48rpx;
			border-radius: 50%;
			background: rgba(255, 255, 255, 0.3);
			line-height: 50rpx;
			image{
				width: 28rpx;
				height: 28rpx;
			}
		}
		.head-left{
			left: 10%;
		}
		.head-right{
			right: 10%;
		}
	}
    .list1{
		margin: 40rpx auto;
		width:630rpx;
		background:rgba(255,255,255,1);
		box-shadow:0px 12rpx 28rpx rgba(0,0,0,0.08);
		border-radius:12rpx;
		padding: 30rpx 20rpx;
		.list1-li{
			font-size: 28rpx;
			height: 52rpx;
			line-height: 52rpx;
			color: #595959;
			text{
				display: inline-block;
				width: 200rpx;
				color: #8C8C8C;
			}
		}
		.dizhi{
			height: auto;
			line-height: 52rpx;
			.wizhi{
				float: left;
			}
			.dibox{
				display: inline-block;
				width: calc(100% - 200rpx);;
			}
		}
	}
	.listbox{
		.list2,.list3{
			margin: 20rpx auto;
			width:630rpx;
			height:336rpx;
			background:rgba(255,255,255,1);
			box-shadow:0px 12rpx 28rpx rgba(0,0,0,0.08);
			border-radius:12rpx;
			padding: 0rpx 20rpx 30rpx;
			.list2-li1{
				font-size: 28rpx;
				height: 52rpx;
				line-height: 52rpx;
				color: #595959;
				text{
					display: inline-block;
					width: 200rpx;
					color: #8C8C8C;
				}
			}
		}
		.list3{
			margin-top: 10rpx;
			height:736rpx;
		}
		.listfujian{
			margin: 20rpx auto;
			width:630rpx;
			background:rgba(255,255,255,1);
			box-shadow:0px 12rpx 28rpx rgba(0,0,0,0.08);
			border-radius:12rpx;
			padding: 0rpx 20rpx 30rpx;
			.listfujian-top{
				.listfujian-textarea{
					margin-top: 20rpx;
					height:272rpx;
					padding: 20rpx;
					background:rgba(245,245,245,1);
					opacity:1;
					border-radius:12rpx;
				}
			}
			.listfujian-cen{
				text{
					height:64rpx;
					margin-right: 20rpx;
					margin-top: 20rpx;
					display: inline-block;
					padding: 0 20rpx;
					font-size:24rpx;
					font-weight:400;
					line-height:64rpx;
					color:rgba(140,140,140,1);
					background:rgba(245,245,245,1);
					box-shadow:0px 6px 14px rgba(0,0,0,0.08);
					border-radius:12rpx;
				}
			}
			.listfujian-img{
				margin-top: 20rpx;
				.uni-uploader-body{
					padding: 20rpx 0;
					overflow: hidden;
					.uni-uploader__file{
						position: relative;
						width: 160rpx;
						height: 160rpx;
						float: left;
						margin-right: 20rpx;
						.uni-uploader__img{
							width: 160rpx;
							background:rgba(245,245,245,1);
							border-radius:12rpx;
							height: 160rpx;
						}
						.iconqingchu{
							position: absolute;
							top:-20rpx;
							right: 0rpx;
							color: #979797;
						}
					}
					.uni-uploader__input-box{
						float: left;
						.uni-uploader__input{
							width: 160rpx;
							background:rgba(245,245,245,1);
							border-radius:12rpx;
							height: 160rpx;
							text-align: center;
							color: #979797;
							.icontianjia{
								padding-top: 16rpx;
								font-size: 40rpx;
								margin-bottom: 10rpx;
								display: block;
							}
							text{
								font-size: 24rpx;
							}
						}
					}
				}
			}
		    .uni-btn-v{
		    	padding-bottom: 30rpx;
		    	button{
		    		// width: 60%;
		    		background:rgba(117,194,58,1);
		    		border-radius:8rpx;
		    		height: 80rpx;
		    		width: 368rpx;
		    		color: #FFFFFF;
		    		margin-top: 40rpx;
		    	}
		    }
		}
		.listfiles{
			margin: 20rpx auto 100rpx;
			width:630rpx;
			background:rgba(255,255,255,1);
			box-shadow:0px 12rpx 28rpx rgba(0,0,0,0.08);
			border-radius:12rpx;
			padding: 0rpx 20rpx 30rpx;
			.listf{
				.listfi{
					height: 60rpx;
					line-height: 60rpx;
					color: #404040;
					font-size: 28rpx;
					position: relative;
					.iconxiazai{
						position: absolute;
						top: 0rpx;
						right:0rpx;
						color: #979797;
					}
				}
			}
		}
	}
}
/* #ifndef APP-PLUS */
    page {
        width: 100%;
		height: 100%;
        min-height: 100%;
        display: flex;
    }

    /* #endif */

    .tabs {
        flex: 1;
        flex-direction: column;
        overflow: hidden;
        background-color: #ffffff;
        /* #ifdef MP-ALIPAY || MP-BAIDU */
        height: 100vh;
        /* #endif */
    }

    .scroll-h {
        width: 750rpx;
        height: 6vh;
		margin-left: 25rpx;
        flex-direction: row;
        /* #ifndef APP-PLUS */
        white-space: nowrap;
        /* #endif */
        /* flex-wrap: nowrap; */
        /* border-color: #cccccc;
		border-bottom-style: solid;
		border-bottom-width: 1px; */
    }

    .line-h {
        height: 1rpx;
        background-color: #cccccc;
    }
    .uni-tab-item {
        /* #ifndef APP-PLUS */
        display: inline-block;
        /* #endif */
        flex-wrap: nowrap;
        padding-left: 25rpx;
        padding-right: 25rpx;
		position: relative;
		.bian{
			width: 30%;
			height: 6rpx;
			background-color: #83C353;
			border-radius: 2rpx;
			position: absolute;
			left: 50%;
			bottom: 6rpx;
			-webkit-transform: translateX(-50%);
			transform: translateX(-50%);
			-webkit-transition: .3s;
			transition: .3s;
		}
    }
	

    .uni-tab-item-title {
        color: #404040;
        font-size: 28rpx;
        height: 6vh;
        line-height: 6vh;
        flex-wrap: nowrap;
        /* #ifndef APP-PLUS */
        white-space: nowrap;
        /* #endif */
    }

    .uni-tab-item-title-active {
        color: #83C353;
    }

    .swiper-box {
        flex: 1;
		height: 84vh;
    }

    .swiper-item {
        flex: 1;
        flex-direction: row;
    }

    .scroll-v {
        flex: 1;
		height: 100%;
        /* #ifndef MP-ALIPAY */
        flex-direction: column;
        /* #endif */
        width: 750rpx;
    }

    .update-tips {
        position: absolute;
        left: 0;
        top: 41px;
        right: 0;
        padding-top: 5px;
        padding-bottom: 5px;
        background-color: #FDDD9B;
        align-items: center;
        justify-content: center;
        text-align: center;
    }

    .update-tips-text {
        font-size: 14px;
        color: #ffffff;
    }

    .refresh {
        width: 750rpx;
        height: 64px;
        justify-content: center;
    }

    .refresh-view {
        flex-direction: row;
        flex-wrap: nowrap;
        align-items: center;
        justify-content: center;
    }

	.refresh-icon {
		width: 30px;
		height: 30px;
		transition-duration: .5s;
		transition-property: transform;
		transform: rotate(0deg);
		transform-origin: 15px 15px;
	}

	.refresh-icon-active {
		transform: rotate(180deg);
	}

	.loading-icon {
		width: 20px;
		height: 20px;
		margin-right: 5px;
		color: #999999;
	}

    .loading-text {
        margin-left: 2px;
        font-size: 16px;
        color: #999999;
    }

    .loading-more {
        align-items: center;
        justify-content: center;
        padding-top: 10px;
        padding-bottom: 10px;
        text-align: center;
    }

    .loading-more-text {
        font-size: 28rpx;
        color: #999;
    }
</style>
