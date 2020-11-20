<template>
	<view class="container">
		<view class="t_top"></view>
		
		<!-- 返回顶部 -->
		<view class="to_top" @click="toTop" v-if="isShow"></view>
		
	<!-- 	<view class="head">
			<uni-icons type="back" size="28" @click="toBar"></uni-icons>
			<text class="title">购物车</text>
			<uni-icons type="more" size="26" color="#333"></uni-icons>
		</view> -->
		
		<view class="cart">
			<image src="../../static/imgs/cart/car.png" mode=""></image>
			<text>购物车空空如也，去逛逛吧~</text>
		</view>
		
		<!-- 京东秒杀，分割线 -->
		<view class="split">
			<view class="line1"></view>
			<text>京东秒杀</text>
			<view class="line2"></view>
		</view>
		
		<!-- 京东秒杀 -->
		<view class="seckill_box">
			<view class="kill_head">
				<view class="kill_title">
					<text>京东秒杀</text>
				</view>
				
				<view class="kill_countdown">
					<text>14点场</text>
					<view class="count_box">
						<view class="count_item">00</view>
						<view class="count_item">44</view>
						<view class="count_item">35</view>
					</view>
				</view>
				
				<uni-icons type="forward" color="#ccc" style="margin-left: 300upx;"></uni-icons>
			</view>
			
			<scroll-view class="scroll-view_H" :scroll-x="true" :show-scrollbar = 'false'>
				<view class="kill_con">
					<view class="kill_item" v-for="(item,index) in killList" :key="index">
						<image :src="item.url" mode=""></image>
						<text class="sale">{{item.salePrice}}</text>
						<text class="old">{{item.oldPrice}}</text>
					</view>
					<view class="more_btn">
						<text>查看更多</text>
						<uni-icons type="forward" color="#ccc" style="margin-left: 20upx;margin-top: -20upx;"></uni-icons>
					</view>
				</view>
			</scroll-view>
		</view>
	
		<!-- 可能你还想要分割线 -->
		<view class="split">
			<view class="line1"></view>
			<text>你还想要</text>
			<view class="line2"></view>
		</view>
		
		<!-- want列表 -->
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
				// 是否显示置顶按钮
				isShow:false,
				
				// 京东秒杀列表
				killList:[{
					salePrice:'￥45.00',
					oldPrice:'￥76.00',
					url:'../../static/imgs/kill_img/1.jpg'
				},{
					salePrice:'￥1969.00',
					oldPrice:'￥2299.00',
					url:'../../static/imgs/kill_img/2.jpg'
				},{
					salePrice:'￥319.00',
					oldPrice:'￥490.00',
					url:'../../static/imgs/kill_img/3.jpg'
				},{
					salePrice:'￥99.00',
					oldPrice:'￥179.00',
					url:'../../static/imgs/kill_img/4.jpg'
				},{
					salePrice:'￥79.00',
					oldPrice:'￥00.00',
					url:'../../static/imgs/kill_img/5.jpg'
				},{
					salePrice:'￥99.00',
					oldPrice:'￥129.00',
					url:'../../static/imgs/kill_img/6.jpg'
				},{
					salePrice:'￥278.00',
					oldPrice:'￥378.00',
					url:'../../static/imgs/kill_img/7.jpg'
				},{
					salePrice:'￥799.00',
					oldPrice:'￥1199.00',
					url:'../../static/imgs/kill_img/8.jpg'
				},{
					salePrice:'￥689.00',
					oldPrice:'￥899.00',
					url:'../../static/imgs/kill_img/9.jpg'
				},{
					salePrice:'￥429.00',
					oldPrice:'￥1198.00',
					url:'../../static/imgs/kill_img/10.jpg'
				}],
				
				// 你还想要列表
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
				}],
				
				
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
				  url: '/pages/sort/sort'
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
	page{
		background-color: #f2f2f2;
	}
	
	.container{
		
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
		
		.head{
			width: 750upx;
			height: 88upx;
			background-color: #fff;
			// line-height: 88upx;
			display: flex;
			align-items: center;
			
			.title{
				display: block;
				width: 610upx;
				height: 88upx;
				color: #333;
				text-align: center;
				line-height: 88upx;
				font-size: 34upx;
			}
		}
	
		.cart{
			width: 750upx;
			height: 523upx;
			position: relative;
			
			image{
				width: 180upx;
				height: 180upx;
				top: 0;
				left: 0;
				bottom: 0;
				right: 0;
				margin: auto;
				position: absolute;
			}
			
			text{
				position: absolute;
				left: 180upx;
				top: 380upx;
			}
		}

		.split{
			width: 750upx;
			height: 24upx;
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
		
		.seckill_box{
			margin: 25upx 0 25upx 30upx;
			
			.kill_head{
				width: 731upx;
				height: 70upx;
				background-color: #fff;
				display: flex;
				align-items: center;
				
				.kill_title{
					text{
						color: #333;
						font-size: 32upx;
						font-weight: 700;
						margin: 0 10upx 0 15upx;
					}
				}
				
				.kill_countdown{
					display: flex;
					
					text{
						color: #999;
						font-size: 24upx;
						margin-left: 30upx;
						line-height: 70upx;
					}
					
					.count_box{
						display: flex;
						margin-top: 18upx;
						margin-left: 10upx;
						
						.count_item{
							width: 30upx;
							height: 36upx;
							display: block;
							outline: 0;
							border: 0.2upx  #f2f2f2 solid;
							margin-left: 5upx;
							color: #f2270c;
							font-size: 24upx;
							text-align: center;
						}
					}
					
					
				}
				
			}
				
			.kill_con{
				width: 1980upx;
				height: 251upx;
				background-color: #fff;
				overflow: hidden;
				
				.kill_item{
					width: 179upx;
					height: 251upx;
					padding: 0 5upx 5upx;
					float: left;
					text-align: center;
					
					image{
						width: 160upx;
						height: 160upx;
					}
					
					.sale{
						color: #f2270c;
						font-size: 32upx;
						margin-top: 10upx;
					}
					
					.old{
						display: block;
						color: #ccc;
						font-size: 24upx;
						text-decoration: line-through;
					}
				}
				
				.more_btn{
					width: 90upx;
					height: 228upx;
					background-color: #f7f7f7;
					float: left;
					
					text{
						width: 36upx;
						height: 136upx;
						display: block;
						margin: 20upx auto;
						color: #999;
						font-size: 24upx;
					}
				}
			}
		}
		
		.want_box{
			margin-top: 40upx;
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
