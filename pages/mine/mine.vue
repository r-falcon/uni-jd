<template>
	<view class="container">
		<view class="t_top"></view>
		
		<!-- 返回顶部 -->
		<view class="to_top" @click="toTop" v-if="isShow"></view>
		
		<!-- <view class="head">
			<uni-icons type="back" size="28" @click="toBar"></uni-icons>
			<text class="title">我的京东</text>
			<uni-icons type="more" size="26" color="#333"></uni-icons>
		</view> -->

		<view class="user_box">
			<view class="user_detail">
				<view class="user_avater">
					<image src="../../static/imgs/mine/user.png" mode=""></image>
				</view>

				<view class="user_info">
					<view class="user">
						<text class="user_id">jd_7208238b93bbc</text>
					</view>

					<view class="tag_btn">
						<text class="btn1">京享值1570</text>
						<text class="btn2">查看小白信用 ></text>
					</view>
				</view>

				<image src="../../static/imgs/mine/settings.png" mode=""></image>
			</view>

			<view class="user_track">
				<view class="track_item" v-for="(item,index) in trackList" :key="index">
					<text class="count">{{item.count}}</text>
					<text class="track_name">{{item.title}}</text>
				</view>
			</view>

			<view class="user_tag">
				<image src="../../static/imgs/mine/tag_icon.png" mode=""></image>
				<text>免费试用 立领1张运费券</text>
				<view class="tag_click">
					<text>0元试用</text>
					<view class="arrow_right"></view>
				</view>
			</view>
		</view>
	
		<view class="user_order">
			<view class="order_box">
				<view class="order_item">
					<image src="../../static/imgs/mine/order/pay.png" mode=""></image>
					<text>待付款</text>
				</view>
				<view class="order_item">
					<image src="../../static/imgs/mine/order/fetch.png" mode=""></image>
					<text>待收货</text>
				</view>
				<view class="order_item">
					<image src="../../static/imgs/mine/order/change.png" mode=""></image>
					<text>退换/售后</text>
				</view>
				<view class="order_all">
					<view class="all_box">
						<image src="../../static/imgs/mine/order/order.png" mode="" style="margin-bottom: 15upx;"></image>
						<text>全部订单</text>
					</view>
				</view>
			</view>
		
			<view class="order_attribute">
				<image src="../../static/imgs/mine/attribute/goods.jpg" mode=""></image>
				
				<view class="desc_box">
					<view class="desc_detail">
						<text>配送中</text>
						<text>2020-11-15 23:40:07</text>
					</view>
					<view class="desc_address">
						<text>{{address.substr(0,25) + '...'}}</text>
					</view>
				</view>
			
				
			</view>
		</view>
	
		<view class="property">
			<view class="pty_item">
				<text class="number">2</text>
				<text class="title">优惠券</text>
			</view>
			<view class="pty_item" style="width: 163upx;">
				<text class="number">8,000.000</text>
				<text class="title">白条额度</text>
			</view>
			<view class="pty_item">
				<text class="number">60</text>
				<text class="title">京豆</text>
			</view>
			<view class="pty_item">
				<text class="number">0</text>
				<text class="title">红包</text>
			</view>
			<view class="pty_pay">
				<view class="pty_box">
					<image src="../../static/imgs/mine/property/pty.png" mode=""></image>
					<text class="title">优惠券</text>
				</view>
			</view>
		</view>
		
		<view class="tools_box">
			<text class="title">工具与服务</text>
			
			<view class="item_box">
				<view class="tools_item" v-for="(item,index) in toolsList" :key="index">
					<image :src="item.url" mode=""></image>
					<text>{{item.title}}</text>
				</view>
			</view>
		</view>
	
		<view class="split">
			<view class="line1"></view>
			<text>为您推荐</text>
			<view class="line2"></view>
		</view>
	
		<view class="want_box">
			<view class="want_item" v-for="(item,index) in wantList" :key="index">
				<image :src="item.url" mode="" class="want_img"></image>
				<image :src="item.icon" mode="" class="db_icon"></image>
				<text class="want_title">{{item.title.substr(0,20) + '...'}}</text>
				<view class="buy_box">
					<text class="price">{{item.price}}</text>
					<view class="tags">{{item.tips}}</view>
					<image :src="item.cartIcon" mode=""></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				// 是否显示置顶
				isShow:false,
				
				address:'[石家庄市]【河北省石家庄市裕华区富强大街公司】 派件中  派件人: 刘金宝 电话 18521189365  如有疑问，请联系：19932172717',
				
				// 用户足迹列表
				trackList:[{
					count:0,
					title:'商品收藏'
				},{
					count:1,
					title:'店铺收藏'
				},{
					count:0,
					title:'我的足迹'
				}],
				
				// 服务与工具列表
				toolsList:[{
					url:'../../static/imgs/mine/tools/1.png',
					title:'客户服务'
				},{
					url:'../../static/imgs/mine/tools/2.png',
					title:'我的预约'
				},{
					url:'../../static/imgs/mine/tools/3.png',
					title:'高价回收'
				},{
					url:'../../static/imgs/mine/tools/4.png',
					title:'京东火车票'
				},{
					url:'../../static/imgs/mine/tools/5.png',
					title:'应用推荐'
				},{
					url:'../../static/imgs/mine/tools/6.png',
					title:'京东机票'
				},{
					url:'../../static/imgs/mine/tools/7.png',
					title:'京东酒店'
				},{
					url:'../../static/imgs/mine/tools/8.png',
					title:'闲置换钱'
				},{
					url:'../../static/imgs/mine/tools/9.png',
					title:'定期购'
				}],
				
				wantList:[{
					url:'../../static/imgs/want/1.jpg',
					icon:'../../static/imgs/commend/cm_icon/db11.png',
					title:'九叶草氨基酸洗面奶男女通用控油去黑头敏感肌深层清洁收缩毛孔温和洁面乳 1瓶装【洗面奶体验装】',
					price:'￥39',
					cartIcon:'../../static/imgs/want/cart.png',
					tips:'满减'
				},{
					url:'../../static/imgs/want/2.jpg',
					icon:'../../static/imgs/commend/cm_icon/db11.png',
					title:'华硕（ASUS）RT-AX86U双频5700M全千兆路由无线路由器/一键性能手游加速/2.5G端口/WiFi6',
					price:'￥1399',
					cartIcon:'../../static/imgs/want/cart.png',
					tips:'秒杀'
				},{
					url:'../../static/imgs/want/3.jpg',
					icon:'../../static/imgs/commend/cm_icon/db11.png',
					title:'法国碧欧泉（BIOTHERM）男士净肤细致护肤品礼盒套装(洁面膏125ml+爽肤水200ml+保湿露50ml 控油洗面奶)',
					price:'￥800',
					cartIcon:'../../static/imgs/want/cart.png',
					tips:'券'
				},{
					url:'../../static/imgs/want/4.jpg',
					icon:'../../static/imgs/commend/cm_icon/db11.png',
					title:'松下 大1匹 直流变频 冷暖壁挂式家用空调挂机 SE9KJ1S （象牙白）（KFR-26GW/BpSJ1S）（panasonic）',
					price:'￥2548',
					cartIcon:'../../static/imgs/want/cart.png',
					tips:'闪购'
				}]
			};
		},
		
		// 监听页面滚动事件
		onPageScroll(e){
			this.scrollHeight = e.scrollTop
			
			if(this.scrollHeight > 200){
				this.isShow = true
			}else{
				this.isShow = false
			}
		},
		
		// 自定义导航栏的点击事件
		onNavigationBarButtonTap(e) {
			if(e.index === 0){
				uni.switchTab({
				  url: '/pages/index/index'
				})
			}else{
				uni.switchTab({
				  url: '/pages/find/find'
				})
			}
		},
		
		
		methods:{
			// 返回顶部操作
			toTop(){
				uni.pageScrollTo({
					scrollTop:0
				})
			},
			
			// 返回index页面
			toBar(){
				uni.switchTab({
				  url: '/pages/index/index'
				})
			}
		}
	
	}
</script>

<style lang="scss" scoped>
	page {
		background-color: #f2f2f2;
	}

	.container {
		// .t_top{
		// 	width: 750upx;
		// 	height: 88upx;
		// 	background-color: #fff;
		// }
		
		.to_top{
			// display: none;
			display: block;
			width: 76upx;
			height: 76upx;
			border-radius: 50%;
			background: url(../../static/imgs/toTop/top.png) no-repeat;
			background-size: cover;
			position: fixed;
			z-index: 20;
			left: 670upx;
			top: 1200upx;
		}
		
		.head {
			width: 750upx;
			height: 88upx;
			background-color: #fff;
			// line-height: 88upx;
			display: flex;
			align-items: center;

			.title {
				display: block;
				width: 610upx;
				height: 88upx;
				color: #333;
				text-align: center;
				line-height: 88upx;
				font-size: 34upx;
			}
		}

		.user_box {
			width: 740upx;
			height: 380upx;
			margin: 0 auto;
			background: url(../../static/imgs/mine/bg.png) no-repeat;
			background-size: cover;

			.user_detail {
				width: 740upx;
				height: 120upx;
				display: flex;
				align-items: center;
				padding: 0 0 36upx 36upx;

				.user_avater {
					width: 104upx;
					height: 104upx;
					border: 2upx solid #fff;
					border-radius: 50%;
					margin-top: 20upx;

					image {
						display: block;
						width: 100upx;
						height: 100upx;
						margin: 2upx auto;
					}
				}

				.user_info {
					padding: 0 0 0 30upx;

					.user {
						.user_id {
							height: 80upx;
							color: #fff;
							font-size: 36upx;
							line-height: 80upx;

							&::after {
								content: "";
								display: inline-block;
								width: 30upx;
								height: 30upx;
								background: url(../../static/imgs/mine/icon.png) no-repeat scroll -30upx 0/cover;
								margin-left: 10upx;
							}
						}
					}

					.tag_btn {
						display: flex;
						align-items: center;

						.btn1,
						.btn2 {
							display: block;
							color: #fff;
							font-size: 18upx;
							background: rgba(0, 0, 0, 0.16);
							border-radius: 20upx;
							text-align: center;
							line-height: 32upx;
							padding: 0 16upx;
							margin: 0 12upx 0 0;
						}

						.btn1 {
							width: 140upx;
							height: 32upx;
						}

						.btn2 {
							width: 170upx;
							height: 32upx;
						}
					}
				}

				image {
					width: 40upx;
					height: 40upx;
					margin-left: 100upx;
					margin: -20upx 0 0 100upx;
				}
			}

			.user_track {
				display: flex;
				align-items: center;
				justify-content: space-around;

				.track_item {
					text-align: center;

					.count {
						display: block;
						font-size: 30upx;
						font-weight: 700;
						margin-bottom: 10upx;
					}

					.track_name {
						margin-top: 10upx;
						font-size: 24upx;
					}

					.count,
					.track_name {
						color: #fff;
					}
				}
			}

			.user_tag {
				width: 680upx;
				height: 84upx;
				background: url(../../static/imgs/mine/tab_bg.png) no-repeat;
				background-size: cover;
				margin: 30upx auto 0;
				display: flex;
				align-items: center;
				position: relative;

				image {
					margin-left: 20upx;
					width: 114upx;
					height: 24upx;
				}

				text {
					margin-left: 40upx;
					color: #ffe678;
					font-size: 24upx;

					&::before {
						position: absolute;
						content: '';
						display: block;
						width: 2upx;
						height: 14upx;
						background-color: #ffe678;
						top: 35upx;
						left: 154upx;
					}
				}

				.tag_click {
					width: 150upx;
					height: 36upx;
					background-image: -webkit-linear-gradient(140deg, #ffe36f, #f6d44e);
					border-radius: 18upx;
					margin-left: 80upx;
					line-height: 36upx;
					display: flex;
					align-items: center;

					text {
						margin-left: 24upx;
						color: #262626;
						font-size: 22upx;
					}

					.arrow_right {
						width: 0;
						height: 0;
						border-top: 8upx solid transparent;
						border-bottom: 8upx solid transparent;
						border-left: 8upx solid #262626;
						margin-left: 10upx;
						margin-top: -2upx;
					}
				}
			}
		}
		
		.user_order{
			width: 740upx;
			height: 320upx;
			margin: 0 auto;
			background-color: #fff;
			border-radius: 24upx;
			margin-top: -20upx;
			
			.order_box{
				padding:25upx 30upx 0;
				width: 690upx;
				height: 160upx;
				display: flex;
				align-items: center;
				justify-content: space-around;
				
				.order_item,.order_all{
					width: 174upx;
					text-align: center;
					
					image{
						display: block;
						width: 60upx;
						height: 60upx;
						margin: 0 auto;
					}
					
					text{
						color: #262626;
						font-size: 22upx;
					}
				}	
				
				.order_all{
					display: flex;
					
					.all_box{
						margin-left: 40upx;
						margin-top: 25upx;
					}
				}
				
				.order_all::before{
					content: '';
					display: block;
					width: 20upx;
					height: 144upx;
					background: url(../../static/imgs/mine/after.png) no-repeat;
					background-size: cover;
				}
			}
			
			
			.order_attribute{
				margin: 0 auto;
				width: 680upx;
				height: 140upx;
				border-top: 1upx solid #f2f2f2;
				display: flex;
				align-items: center;
				
				image{
					display: block;
					width: 80upx;
					height: 80upx;
				}
				
				.desc_box{
					margin-left: 20upx;
					
					.desc_detail{
						color: #999;
						font-size: 24upx;
						
						text:nth-child(1){
							margin-right: 20upx;
							color: #e93b3d;
							font-size: 28upx;
						}
					}
					
					.desc_address{
						margin-top: 10upx;
						color: #999;
						font-size: 24upx;
					}
				}
				
				
			}
		}
		
		.property{
			padding: 0 0 0 20upx;
			width: 732upx;
			height: 160upx;
			background-color: #fff;
			border-radius: 24upx;
			margin-top: 30upx;
			display: flex;
			align-items: center;
			
			.pty_item,.pty_pay{
				width: 133upx;
				text-align: center;
				
				.number{
					display: block;
					color: #262626;
					font-weight: 700;
					font-family: JDZhengHT-Regular;
				}
				.title{
					color: #262626;
					font-size: 22upx;
				}
			}
			
			.pty_pay{
				display: flex;
				
				.pty_box{
					margin-top: 20upx;
					margin-left: 20upx;
					
					image{
						margin: 0 auto;
						display: block;
						width: 60upx;
						height: 60upx;
					}
				}
				
				&::before{
					content: '';
					display: block;
					width: 20upx;
					height: 144upx;
					background: url(../../static/imgs/mine/after.png) no-repeat;
					background-size: cover;
				}
			}
		}
		
		.tools_box{
			width: 740upx;
			margin: 0 auto;
			height: 540upx;
			background-color: #fff;
			border-radius: 24upx;
			margin: 30upx auto;
			
			.title{
				color: #2e2d2d;
				font-size: 28upx;
				font-weight: 700;
				padding-left: 36upx;
				line-height: 80upx;
			}
			
			.item_box{
				width: 740upx;
				height: 464upx;
				margin: 0 auto;
				border-top: 1upx solid #f2f2f2;
				overflow: hidden;
				
				
				
				.tools_item{
					width: 25%;
					text-align: center;
					float: left;
					margin: 24upx auto 0;
					
					image{
						width: 70upx;
						height: 70upx;
					}
					
					text{
						margin-top: 10upx;
						display: block;
						color: #262626;
						font-size: 24upx;
					}
					
				}
			}
		}
	
		.split{
			width: 740upx;
			height: 24upx;
			margin: 0 auto;
			display: flex;
			align-items: center;
			justify-content: space-around;
			position: relative;
			
			.line1,.line2{
				width: 280upx;
				height: 2upx;
				background-color: #ccc;
			}
			
			text{
				color: #666;
				font-size: 24upx;
				
				&::after,&::before{
					content: '';
					position: absolute;
					width: 8upx;
					height: 8upx;
					background-color: #ccc;
					border-radius: 50%;
					top: 50%;
					transform: rotate(45deg);
					margin-top: -4upx;
				}
				
				&::after{
					margin-left: 32upx;
				}
				
				&::before{
					margin-left: -32upx;
				}
			}
		}
	
		.want_box{
			margin: 30upx auto;
			overflow: hidden;
			
			.want_item{
				width: 374upx;
				height: 496upx;
				background-color: #fff;
				margin-bottom: 2upx;
				float: left;
				border-radius: 20upx;
				
				&:nth-child(2n){
					margin-left: 2upx;
				}
				
				image{
					width: 315upx;
					height: 315upx;
					margin-top: 30upx;
					margin-left: 30upx;
				}
				
				.db_icon{
					// display: block;
					width: 39upx;
					height: 26upx;
					float: left;
				}
				
				.want_title{
					display: block;
					color: #333;
					font-size: 24upx;
					// margin-left: 40upx;
					margin-top: 15upx;
					padding-left: 76upx;
				}
				
				.buy_box{
					display: flex;
					align-items: center;
					margin-top: 10upx;
					
					.price{
						color: #e93b3d;
						font-size: 32upx;
						margin-left: 30upx;
					}
					
					.tags{
						width: 50upx;
						height: 30upx;
						border: 1upx #e4393c solid;
						color: #e4393c;
						font-size: 18upx;
						text-align: center;
						line-height: 30upx;
						border-radius: 4upx;
						margin-left: 15upx;
					}
					
					image{
						width: 35upx;
						height: 30upx;
						margin-left: 100upx;
						margin-top: -1upx;
					}
				}
			}
		}
	}
</style>
