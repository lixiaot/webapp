<template>
	<view class="uni-popup-dialog">
		<view class="newadd">
			<text>新增器具</text><icon @click="close" class="iconfont iconguanbi" />
		</view>
		<view class="listtable">
			<form @submit="formSubmit" >
				<view class="uni-form-item uni-column">
					<text class="title">器具编号<text>*</text></text>
					<input class="uni-input" name="coding" placeholder="请输入" />
				</view>
				<view class="uni-form-item uni-column">
					<text class="title">器具别名</text>
					<input class="uni-input" placeholder="请输入" />
				</view>
				<view class="uni-form-item uni-column">
					<text class="title">型号规格</text>
					<input class="uni-input" placeholder="请输入" />
				</view>
				<view class="uni-form-item uni-column">
					<text class="title">设备分类</text>
					<input class="uni-input" placeholder="请输入" />
				</view>
				<view class="uni-form-item uni-column">
					<text class="title">出厂编号</text>
					<input class="uni-input" placeholder="请输入" />
				</view>
				<view class="uni-form-item uni-column">
					<text class="title">主检科室</text>
					<input class="uni-input" placeholder="请输入" />
				</view>
				<view class="uni-form-item uni-column">
					<text space class="title">备注</text>
					<input class="uni-input" placeholder="请输入" />
				</view>
				<view class="uni-btn-v">
					<button form-type="submit">保存</button>
				</view>
			</form>
		</view>
		<!-- <view class="uni-dialog-button-group">
			<view class="uni-dialog-button" @click="close">
				<text class="uni-dialog-button-text">取消</text>
			</view>
			<view class="uni-dialog-button uni-border-left" @click="onOk">
				<text class="uni-dialog-button-text uni-button-color">确定</text>
			</view>
		</view> -->

	</view>
</template>

<script>
	var  graceChecker = require("../../common/graceChecker.js");
	export default {
		name: "uniPopupDialog",
		props: {},
		data() {
			return {
				dialogType: 'error',
				focus: false,
				val: ""
			}
		},
		inject: ['popup'],
		created() {
			// 对话框遮罩不可点击
			this.popup.mkclick = false
		},
		methods: {
			formSubmit: function(e) {
				console.log('form发生了submit事件，携带数据为：' + JSON.stringify(e.detail.value))
			    //定义表单规则
			    var rule = [
			        {name:"coding", checkType : "string", checkRule:"",  errorMsg:"编码不能为空"},
			    ];
			    //进行表单检查
			    var formData = e.detail.value;
			    var checkRes = graceChecker.check(formData, rule);
			    if(checkRes){
			        uni.showToast({title:"验证通过!", icon:"none"});
			    }else{
			        uni.showToast({ title: graceChecker.error, icon: "none" });
			    }
			},
			/**
			 * 点击确认按钮
			 */
			onOk() {
				this.$emit('confirm', () => {
					this.popup.close()
					if (this.mode === 'input') this.val = this.value
				}, this.mode === 'input' ? this.val : '')
			},
			/**
			 * 点击取消按钮
			 */
			close() {
				if (this.beforeClose) {
					this.$emit('close', () => {
						this.popup.close()
					})
					return
				}
				this.popup.close()
			}
		}
	}
</script>

<style lang="scss" scoped>
	.uni-popup-dialog{
		background-color: #FFFFFF;
		width: 670rpx;
		border-radius:12rpx;
		.newadd{
			height: 96rpx;
			line-height: 96rpx;
			padding: 0 20rpx;
			border-bottom:1px solid rgba(230,230,230,1);
			text{
				font-size:32rpx;
				font-weight:800;
				color:rgba(38,38,38,1);
			}
			.iconguanbi{
				font-size:32rpx;
				color:#979797;
				float: right;
			}
		}
	    .listtable{
			.uni-form-item{
				padding: 0 20rpx;
				height: 112rpx;
				line-height: 112rpx;
				font-size: 32rpx;
				margin-left: 5%;
				border-bottom:1px solid rgba(230,230,230,1);
				.title{
					// padding-left: 5%;
					display: inline-block;
					width: 30%;
					float: left;
					color: #8C8C8C;
					text{
						color: #FF656D;
					}
				}
				.uni-input{
					display: inline-block;
					width: 70%;
					float: left;
					height: 112rpx;
					line-height: 112rpx;
				}
			}
			.uni-btn-v{
				padding-bottom: 30rpx;
				button{
					// width: 60%;
					background:rgba(117,194,58,1);
					border-radius:8rpx;
					height: 80rpx;
					line-height: 80rpx;
					width: 368rpx;
					color: #FFFFFF;
					margin-top: 40rpx;
				}
			}
		}
	}	
</style>