<script>
export default {
	onLaunch: function() {
		// console.log('App Launch');
	},
	onShow: function() {
		// console.log('App Show');
	},
	onHide: function() {
		// console.log('App Hide');
	}
};
</script>

<style>
/* 解决头条小程序组件内引入字体不生效的问题 */
/* #ifdef MP-TOUTIAO */
@font-face {
	font-family: uniicons;
	src: url('/static/uni.ttf');
}
/* #endif */

@font-face {
  font-family: 'iconfont';  /* project id 2006533 */
  src: url('//at.alicdn.com/t/font_2006533_yookenitagl.eot');
  src: url('//at.alicdn.com/t/font_2006533_yookenitagl.eot?#iefix') format('embedded-opentype'),
  url('//at.alicdn.com/t/font_2006533_yookenitagl.woff2') format('woff2'),
  url('//at.alicdn.com/t/font_2006533_yookenitagl.woff') format('woff'),
  url('//at.alicdn.com/t/font_2006533_yookenitagl.ttf') format('truetype'),
  url('//at.alicdn.com/t/font_2006533_yookenitagl.svg#iconfont') format('svg');
}
.iconfont {
	font-family: 'iconfont' !important;
	font-size: 32rpx;
	font-style: normal;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
}
.iconsaoyisao:before {
	content: '\e605';
}

.iconrili:before {
	content: '\e606';
}
.icongouxuan:before {
	content: '\e607';
}
.iconjiantou:before {
	content: '\e608';
}
.iconsousuo:before {
	content: '\e609';
}
.icontianjia:before {
	content: '\e60a';
}
.iconguanbi:before {
	content: '\e60b';
}
.iconqingchu:before {
	content: '\e60c';
}
.iconfujian:before {
	content: '\e60d';
}

.icontianjiamoumouxiangmu:before {
	content: '\e60e';
}
.iconjingshitubiao:before {
	content: '\e60f';
}

.iconshoufaruku:before {
	content: '\e601';
}
.iconsongrukeshi:before {
	content: '\e602';
}
.iconfanhuishoufa:before {
	content: '\e603';
}
.iconchuku:before {
	content: '\e604';
}
.icondayin:before {
	content: '\e600';
}
.iconxiazai:before {
	content: '\e613';
}
.iconshouji:before {
	content: '\e610';
}
.icongerenzhongxin:before {
	content: '\e611';
}
.iconjiantou-copy:before {
	content: '\e612';
}
checkbox .wx-checkbox-input {
	border-radius: 50% !important;
	color: #ffffff !important;
}

checkbox .wx-checkbox-input.wx-checkbox-input-checked {
	color: #fff;
	border-color: #83c353;
	background: #83c353;
}
checkbox .wx.uni-checkbox-input-checked:after {
	font-size: 14px;
}
</style>
