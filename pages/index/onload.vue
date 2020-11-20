<template>
	<view class="container">
		<view class="top_box">
			<image src="../../static/imgs/onLoad/logo.png" mode=""></image>
		</view>
		<view class="tips_box">
			<text class="tips1">京东购物 实惠轻松</text>
			<text class="tips2">新用户享188元大礼包</text>
			<button class="btn">iPhone版本下载</button>
		</view>
		<view class="bottom_box"></view>
	</view>
</template>

<script>
</script>

<style lang="scss" scoped>
	page{
		background-color: #f23030;
	}
	
	.container{
		background-color: #fff;
		// background-color: #f23030;
		
		.top_box{
			width: 750upx;
			height: 586upx;
			background: #fff url(../../static/imgs/onLoad/bg1.png) no-repeat;
			background-size: 600upx 586upx;
			background-position: 70upx 0;
			overflow: hidden;
			
			image{
				display: block;
				width: 150upx;
				height: 150upx;
				margin: 250upx auto;
				
			}
		}
		
		.tips_box{
			width: 750upx;
			height: 357upx;
			background: url(../../static/imgs/onLoad/bg2.png) no-repeat;
			background-size: cover;
			position: relative;
			
			.tips1,.tips2{
				position: absolute;
			}
			
			.tips1{
				color: #fff;
				font-weight: 700;
				font-size: 42upx;
				left: 200upx;
				top: 80upx;
			}
			
			.tips2{
				color: #fff;
				font-weight: 700;
				font-size: 32upx;
				left: 210upx;
				top: 160upx;
			}
			
			.btn{
				width: 676upx;
				height: 70upx;
				background-color: #fff;
				border-radius: 6upx;
				color: #f23030;
				font-size: 28upx;
				font-weight: bold;
				text-align: center;
				line-height: 70upx;
				top: 280upx;
			}
		}
	
		.bottom_box{
			width: 750upx;
			height: 300upx;
			background-color: #f23030;
		}
	}
</style>
