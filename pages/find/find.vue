<template>
	<view class="container">
		<!-- 头部 -->
		<view class="head_box">
			<view class="head_item">
				<image src="../../static/imgs/find/mine.png" mode="" class="user" @click="toBar"></image>
				<image src="../../static/imgs/find/find1.png" mode="" class="gift1"></image>
				<!-- <image src="../../static/imgs/find/search.png" mode="" class="search"></image> -->
				<image src="../../static/imgs/find/message.png" mode="" class="message"></image>
			</view>
			
			<view class="head_nav">
				<view class="nav_item" v-for="(item,index) in navList" :key="index">
					{{item}}
				</view>
			</view>
		</view>
		
		<!-- 推荐店铺 -->
		<view class="cmd_box">
			<view class="cmd_title">
				<image src="../../static/imgs/find/item/icon.jpg" mode=""></image>
				<text>无印良品MUJI  官方旗舰店</text>
			</view>
			
			<scroll-view class="scroll-view_H" :scroll-x="true" :show-scrollbar="false">
				<view class="kill_con">
					<view class="kill_item" v-for="(item,index) in killList" :key="index">
						<image :src="item.url" mode=""></image>
						<text class="title">{{item.title.substr(0,7) + '...'}}</text>
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
	
		<!-- 其他推荐 -->
		<view class="other_cmd">
			<view class="other_item" v-for="(item,index) in cmdList" :key="index">
				<view class="other_head">
					<image :src="item.icon" mode="" class="icon"></image>
					<text>{{item.title}}</text>
					<button class="btn">
						<image :src="item.attention" mode=""></image>
						<text>关注</text>
					</button>
				</view>
				
				<view class="other_con">
					<view class="left">
						<image :src="item.img" mode=""></image>
					</view>
					
					<view class="right">
						<text class="desc">{{item.desc}}</text>
						<text class="price">{{item.price}}</text>
					</view>
				</view>
				
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				// 导航栏
				navList:['关注','看一看','视频','5G','直播'],
				
				// 店铺推荐列表
				killList:[{
					salePrice:'￥45.00',
					oldPrice:'￥76.00',
					url:'../../static/imgs/kill_img/1.jpg',
					title:' 无印良品MUJI 基础润肤化妆水 爽肤水 补水 清爽型 200ml'
				},{
					salePrice:'￥1969.00',
					oldPrice:'￥2299.00',
					url:'../../static/imgs/kill_img/2.jpg',
					title:' 无印良品MUJI 基础润肤化妆水 爽肤水 补水 清爽型 200ml'
				},{
					salePrice:'￥319.00',
					oldPrice:'￥490.00',
					url:'../../static/imgs/kill_img/3.jpg',
					title:' 无印良品MUJI 基础润肤化妆水 爽肤水 补水 清爽型 200ml'
				},{
					salePrice:'￥99.00',
					oldPrice:'￥179.00',
					url:'../../static/imgs/kill_img/4.jpg',
					title:' 无印良品MUJI 基础润肤化妆水 爽肤水 补水 清爽型 200ml'
				},{
					salePrice:'￥79.00',
					oldPrice:'￥00.00',
					url:'../../static/imgs/kill_img/5.jpg',
					title:' 无印良品MUJI 基础润肤化妆水 爽肤水 补水 清爽型 200ml'
				},{
					salePrice:'￥99.00',
					oldPrice:'￥129.00',
					url:'../../static/imgs/kill_img/6.jpg',
					title:' 无印良品MUJI 基础润肤化妆水 爽肤水 补水 清爽型 200ml'
				},{
					salePrice:'￥278.00',
					oldPrice:'￥378.00',
					url:'../../static/imgs/kill_img/7.jpg',
					title:' 无印良品MUJI 基础润肤化妆水 爽肤水 补水 清爽型 200ml'
				},{
					salePrice:'￥799.00',
					oldPrice:'￥1199.00',
					url:'../../static/imgs/kill_img/8.jpg',
					title:' 无印良品MUJI 基础润肤化妆水 爽肤水 补水 清爽型 200ml'
				},{
					salePrice:'￥689.00',
					oldPrice:'￥899.00',
					url:'../../static/imgs/kill_img/9.jpg',
					title:' 无印良品MUJI 基础润肤化妆水 爽肤水 补水 清爽型 200ml'
				},{
					salePrice:'￥429.00',
					oldPrice:'￥1198.00',
					url:'../../static/imgs/kill_img/10.jpg',
					title:' 无印良品MUJI 基础润肤化妆水 爽肤水 补水 清爽型 200ml'
				}],
			
				// 其他推荐列表
				cmdList:[{
					icon:'../../static/imgs/find/list/icon1.png',
					img:'../../static/imgs/find/list/img1.jpg',
					title:'华为京东自营官方旗舰店',
					desc:'华为荣耀Play4T 华为手机 4000mAh大电池 4800万AI摄影 6.39英寸魅眼屏  幻夜黑 6GB+128GB',
					price:'￥1299.00',
					attention:'../../static/imgs/find/attention.jpg'
				},{
					icon:'../../static/imgs/find/list/icon2.gif',
					img:'../../static/imgs/find/list/img2.jpg',
					title:'小米京东自营旗舰店',
					desc:'小米电视4A 70英寸 4K超高清 HDR 二级能效 2GB+16GB L70M5-4A 内置小爱 智能网络液晶平板教育电视',
					price:'￥3299.00',
					attention:'../../static/imgs/find/attention.jpg'
				}]
			};
		},
		
		// 自定义导航栏的点击事件
		onNavigationBarButtonTap(e) {
			if(e.index === 0){
				uni.switchTab({
				  url: '/pages/sort/sort'
				})
			}else{
				uni.switchTab({
				  url: '/pages/index/index'
				})
			}
		},
		
		methods:{
			// 链接mine页面
			toBar(){
				uni.switchTab({
				  url: '/pages/mine/mine'
				})
			}
		}
	}
</script>

<style lang="scss">
	page{
		background-color: #fff;
	}
	
	.container{
		.head_box{
			width: 750upx;
			height: 500upx;
			margin-top: -50upx;
			background:rgb(243,53,87) url('../../static/imgs/find/find_bg.png') no-repeat;
			background-size: contain;
			background-position: center;
			overflow: hidden;
			
			.head_item{
				width: 750upx;
				height: 100upx;
				margin-top: 100upx;
				display: flex;
				align-items: center;
				
				.user{
					margin-left: 28upx;
					width: 60upx;
					height: 60upx;
				}
				
				.gift1{
					margin-left: 100upx;
					width: 100upx;
					height: 100upx;
				}
				
				// .search{
				// 	margin-left: 310upx;
				// 	width: 50upx;
				// 	height: 50upx;
				// }
				
				.message{
					margin-top: -10upx;
					width: 50upx;
					height: 50upx;
					margin-left: 370upx;
				}
			}
			
			.head_nav{
				width: 750upx;
				height: 70upx;
				background: rgba(243,53,87,0.5);
				display: flex;
				align-items: center;
				justify-content: space-evenly;
				
				.nav_item{
					color: #fff;
					font-weight: 600;
				}
			}
		}
		
		.cmd_box{
			margin: 0 auto;
			margin-top: -190upx;
			width: 730upx;
			height: 500upx;
			background-color: #fff;
			border-top-left-radius: 20upx;
			border-top-right-radius: 20upx;
			
			.cmd_title{
				width: 680upx;
				height: 100upx;
				margin: 0 auto;
				display: flex;
				align-items: center;
				padding: 20upx 0 0 0;
				
				image{
					margin-left: 20upx;
					width: 70upx;
					height: 40upx;
				}
				
				text{
					margin-left: 20upx;
					font-size: 30upx;
					
				}
			}
			
			.kill_con{
				width: 2600upx;
				height: 350upx;
				background-color: #fff;
				overflow: hidden;
				
				.kill_item{
					width: 240upx;
					height: 350upx;
					padding: 0 5upx 5upx;
					float: left;
					text-align: center;
					
					image{
						width: 200upx;
						height: 200upx;
						border-radius: 20upx;
					}
					
					.title{
						width: 190upx;
						display: block;
						color: #333;
						font-size: 28upx;
						margin: 5upx auto 0;
					}
					
					.sale{
						width: 190upx;
						display: block;
						color: #f2270c;
						font-size: 36upx;
						margin-top: 10upx;
						margin: 10upx auto 0;
					}
					
					.old{
						display: block;
						color: #ccc;
						font-size: 28upx;
						text-decoration: line-through;
						margin: 0 auto;
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
	
		.other_cmd{
			width: 750upx;
			margin-top: 50upx;
			
			.other_item{
				width: 730upx;
				height: 420upx;
				margin: 30upx auto;
				
				.other_head{
					width: 670upx;
					height: 80upx;
					margin: 0 auto;
					display: flex;
					align-items: center;
					
					.icon{
						width: 60upx;
						height: 60upx;
					}
					
					text{
						margin-left: 30upx;
						color: #666;
						font-size: 30upx;
					}
					
					.btn{
						margin-right: 20upx;
						width: 162upx;
						height: 60upx;
						background: rgb(243,53,87);
						display: flex;
						align-items: center;
						border-radius: 26upx;
						
						image{
							width: 30upx;
							height: 20upx;
						}
						
						text{
							margin-left: 20upx;
							color: #f2f2f2;
							font-size: 28upx;
						}
					}
				}
			
				.other_con{
					width: 710upx;
					margin: 10upx auto 0;
					display: flex;
					align-items: center;
					
					.left{
						image{
							width: 240upx;
							height: 240upx;
						}
					}
					
					.right{
						margin-left: 30upx;
						
						.desc{
							margin-top: 10upx;
							color: #333;
							font-size: 28upx;
							word-wrap: break-word;
						}
						
						.price{
							margin-top: 30upx;
							display: block;
							color: rgb(243,53,87);
							font-size: 32upx;
						}
					}
					
					
				}
			}
		}
	}
</style>
