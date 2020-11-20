<template>
	<view class="container">
		<view class="t_top"></view>
		
		<!-- iphone下载外链 -->
		<view class="to_load" @click="toPage('./onload')">
			<text class="tips">打开京东APP</text>
		</view>

		<!-- 返回顶部 -->
		<view class="to_top" @click="toTop" v-if="isShow"></view>

		<!-- header -->
		<view class="head_box">
			<view class="head_item">
				<!-- <uni-icons type="jd-list" color="white" size="20" class="jd_list"></uni-icons> -->
				<uni-icons type="jd-icon" color="red" size="18" class="jd_icon"></uni-icons>
				<view class="head_split"></view>
				<uni-icons type="jd-search" color="#ccc" size="20" class="jd_search"></uni-icons>
				<input type="search" value="请输入要搜索的内容" class="head_search" />
				<!-- <uni-icons type="jd-mine" color="white" size="25" class="jd_mine" @click="toBar"></uni-icons> -->
			</view>
		</view>

		<!-- 轮播图 -->
		<swiper class="swiper" :current="imgCurrent" @change="imgChange" :autoplay="true" interval="2000" :indicator-dots="true"
		 indicator-color="#fff" indicator-active-color="rgba(255,49,21,0.7)">
			<swiper-item class="swiper_box" v-for="(item,index) in imgsList" :key="index">
				<image :src="item.url" mode="" class="swiper_item"></image>
			</swiper-item>
		</swiper>

		<!-- 广告区 -->
		<view class="ads">
			<view class="ads_left">
				<image src="../../static/imgs/ads/1.jpg" mode=""></image>
				<text>低至五折</text>
			</view>
			<view class="ads_middle">
				<image src="../../static/imgs/ads/2.jpg" mode="" class="img_first"></image>
				<image src="../../static/imgs/ads/3.jpg" mode="" class="img_second"></image>
			</view>
			<view class="ads_right">
				<image src="../../static/imgs/ads/4.jpg" mode=""></image>
				<text>3件8折</text>
			</view>
		</view>

		<!-- 导航区 -->
		<view class="nav_box">
			<view class="nav_item" v-for="(item,index) in iconList" :key="index">
				<image :src="item.iconUrl" mode=""></image>
				<text>{{item.title}}</text>
			</view>
		</view>

		<!-- 京东秒杀 -->
		<view class="seckill">
			<view class="kill_box">
				<view class="kill_head">
					<text class="kill_title">京东秒杀</text>
					<text class="kill_clock">8</text>
					<image src="../../static/imgs/seckill/clock.png" mode="" class="clock_img"></image>
					<view class="kill_square first">00</view>
					<text class="quote">:</text>
					<view class="kill_square">36</view>
					<text class="quote">:</text>
					<view class="kill_square">24</view>
					<text class="kill_more">更多秒杀</text>
					<image src="../../static/imgs/seckill/kill_more.png" mode="" class="more_img"></image>
				</view>

				<view class="kill_con" v-for="(item,index) in killList" :key="index">
					<image :src="item.img" mode=""></image>
					<text class="sale">{{item.salePrice}}</text>
					<text class="old">{{item.oldPrice}}</text>
				</view>
			</view>
		</view>

		<view class="freshmen">
			<view class="fh_item" v-for="(item,index) in fsList" :key="index">
				<image :src="item.url" mode=""></image>
			</view>
		</view>

		<view class="fh_con">
			<image src="../../static/imgs/freshmen/tag.png" mode=""></image>

			<view class="fh_show">
				<view class="show_item" v-for="(item,index) in showList" :key="index" :style="{backgroundImage:`url(${item.bgUrl})`}">
					<image :src="item.imgUrl" mode=""></image>
					<text class="title" :style="{color:item.titleStyle}">{{item.title}}</text>
					<text class="desc" :style="{color:item.titleStyle}">{{item.desc}}</text>
				</view>
			</view>
		</view>


		<!-- 双11精选会场 -->
		<view class="choice_box">
			<image src="../../static/imgs/double11/1.jpg" mode=""></image>

			<!-- 从右向左滑动 每次一格 -->
			<swiper class="single_box">
				<swiper-item class="single_swiper">
					<view class="single_show" v-for="(item,index) in singleList1" :key="index">
						<view class="single_item" :class="[imgIndex = (index % 2 ) == 0 ? 'bigBox big1' : 'smallBox min2']">
							<image :src="item.url" mode=""></image>
							<text>{{item.title}}</text>
						</view>
					</view>

				</swiper-item>
			</swiper>
			<swiper class="single_box" :autoplay="true" interval="2000">
				<swiper-item class="single_swiper">
					<view class="single_show" v-for="(item,index) in singleList2" :key="index">
						<view class="single_item" :class="[index%2 == 0 ? 'smallBox min1' : 'bigBox big2']">
							<image :src="item.url" mode=""></image>
							<text>{{item.title}}</text>
						</view>
					</view>
				</swiper-item>
			</swiper>

			<!-- swiper切换，每次一屏 -->
			<swiper class="all_box" :autoplay="true" interval="2000">
				<swiper-item v-for="(item,index) in allList" :key="index">
					<view class="all_item">
						<image :src="item.left" mode="" class="all_left" :class=""></image>
						<image :src="item.middle" mode="" class="all_middle"></image>
						<image :src="item.right" mode="" class="all_right"></image>
					</view>
				</swiper-item>
			</swiper>

		</view>

		<!-- 东家小院 -->
		<view class="yard">
			<image src="../../static/imgs/yard/1.jpg" mode="" class="yard_bg"></image>

			<view class="yard_box">
				<view class="yard_item" v-for="(item,index) in yardList1" :key="index">
					<text class="yard_title">{{item.title}}</text>
					<text class="yard_desc">{{item.desc}}</text>
					<view class="yard_show">
						<view class="img_box" v-for="(v,k) in item.url" :key="k">
							<image :src="v.img" mode=""></image>
						</view>
					</view>
				</view>
			</view>

			<view class="yard_list">
				<view class="yard_single" v-for="(item,index) in yardList2" :key="index">
					<text class="title">{{item.title}}</text>
					<text class="desc">{{item.desc}}</text>
					<image :src="item.url" mode=""></image>
				</view>
			</view>
		</view>

		<!-- 每日逛 -->
		<view class="daily_look">
			<image src="../../static/imgs/daily_look/1.jpg" mode=""></image>

			<view class="look_box" v-for="(item,index) in dailyList" :key="index">
				<text class="look_title" :style="{'backgroundImage':`${item.bg}`}">{{item.title}}</text>
				<text class="look_desc">{{item.text}}</text>
				<image :src="item.url" mode=""></image>
			</view>
		</view>


		<!-- 为你推荐 -->
		<view class="cm_box">
			<image src="../../static/imgs/commend/tag.png" mode=""></image>

			<view class="cm_item" v-for="(item,index) in cmList" :key="index">
				<image :src="item.img" mode="" class="item"></image>
				<image :src="item.cmIcon" mode="" class="icon"></image>
				<text class="cm_title">{{item.title.substr(0,20) + '...'}}</text>
				<view class="cm_price">{{item.price}}</view>
				<view class="cm_btn">看相似</view>
			</view>
		</view>
	</view>
</template>

<script>
	import uniIcons from '@/components/uni-icons/uni-icons.vue'

	export default {
		components: {
			uniIcons
		},

		data() {
			return {
				// 是否显示置顶按钮
				isShow:false,
				
				// 轮播图
				imgsList: [{
					url: '../../static/imgs/swiper/1.jpg',
					id: 1
				}, {
					url: '../../static/imgs/swiper/2.jpg',
					id: 2
				}, {
					url: '../../static/imgs/swiper/3.jpg',
					id: 3
				}, {
					url: '../../static/imgs/swiper/4.jpg',
					id: 4
				}],

				// 当前
				imgCurrent: 0,

				// 导航区
				iconList: [{
					id: 5,
					// iconUrl: '../../static/imgs/navs/11.png',
					iconUrl: '../../static/imgs/navs/1.png',
					title: "京东超市"
				}, {
					id: 6,
					// iconUrl: '../../static/imgs/navs/22.png',
					iconUrl: '../../static/imgs/navs/2.png',
					title: "数码电源"
				}, {
					id: 7,
					// iconUrl: '../../static/imgs/navs/33.png',
					iconUrl: '../../static/imgs/navs/3.png',
					title: "京东服饰"
				}, {
					id: 8,
					// iconUrl: '../../static/imgs/navs/44.png',
					iconUrl: '../../static/imgs/navs/4.png',
					title: "京东生鲜"
				}, {
					id: 9,
					// iconUrl: '../../static/imgs/navs/55.png',
					iconUrl: '../../static/imgs/navs/5.png',
					title: "京东到家"
				}, {
					id: 10,
					// iconUrl: '../../static/imgs/navs/66.png',
					iconUrl: '../../static/imgs/navs/6.png',
					title: "充值缴费"
				}, {
					id: 11,
					// iconUrl: '../../static/imgs/navs/77.png',
					iconUrl: '../../static/imgs/navs/7.png',
					title: "9.9元拼"
				}, {
					id: 12,
					// iconUrl: '../../static/imgs/navs/88.png',
					iconUrl: '../../static/imgs/navs/8.png',
					title: "领券"
				}, {
					id: 13,
					// iconUrl: '../../static/imgs/navs/99.png',
					iconUrl: '../../static/imgs/navs/9.png',
					title: "领金贴"
				}, {
					id: 14,
					// iconUrl: '../../static/imgs/navs/00.png',
					iconUrl: '../../static/imgs/navs/0.png',
					title: "PLUS会员"
				}],

				// 秒杀区
				killList: [{
					img: "../../static/imgs/seckill/kill_item/1.jpg",
					salePrice: "￥2480",
					oldPrice: "￥2988"
				}, {
					img: "../../static/imgs/seckill/kill_item/2.jpg",
					salePrice: "￥1290",
					oldPrice: "￥1690"
				}, {
					img: "../../static/imgs/seckill/kill_item/3.jpg",
					salePrice: "￥618",
					oldPrice: "￥699"
				}, {
					img: "../../static/imgs/seckill/kill_item/4.jpg",
					salePrice: "￥2850",
					oldPrice: "￥5999"
				}, {
					img: "../../static/imgs/seckill/kill_item/5.jpg",
					salePrice: "￥1599",
					oldPrice: "￥2299"
				}, {
					img: "../../static/imgs/seckill/kill_item/6.jpg",
					salePrice: "￥1099",
					oldPrice: "￥1299"
				}],

				// 新人专属
				fsList: [{
					id: 15,
					url: "../../static/imgs/freshmen/1.jpg"
				}, {
					id: 16,
					url: "../../static/imgs/freshmen/2.jpg"
				}],

				// 新人福利
				showList: [{
					id: 17,
					bgUrl: '../../static/imgs/freshmen/fh_list/1.jpg',
					imgUrl: '../../static/imgs/freshmen/fh_list/show1.jpg',
					titleStyle: "#7842f2",
					title: '剃须刀榜',
					desc: '999.9万人买过'
				}, {
					id: 18,
					bgUrl: '../../static/imgs/freshmen/fh_list/2.jpg',
					imgUrl: '../../static/imgs/freshmen/fh_list/show2.jpg',
					titleStyle: "#f32d46",
					title: '茶杯榜',
					desc: '30.7万人买过'
				}, {
					id: 19,
					bgUrl: '../../static/imgs/freshmen/fh_list/3.jpg',
					imgUrl: '../../static/imgs/freshmen/fh_list/show3.jpg',
					titleStyle: "#316af2",
					title: '经典童书',
					desc: '孩子爱看'
				}, {
					id: 20,
					bgUrl: '../../static/imgs/freshmen/fh_list/4.jpg',
					imgUrl: '../../static/imgs/freshmen/fh_list/show4.jpg',
					titleStyle: "#f8591a",
					title: '足球动人',
					desc: '诠释轻时代'
				}],

				// // 距离顶部的高度
				// topHeight:0,
				// 页面滚动的距离
				scrollHeight: 0,

				// 精选会场的swiper
				allList: [{
					left: '../../static/imgs/double11/swiper/left1.jpg',
					middle: '../../static/imgs/double11/swiper/middle1.jpg',
					right: '../../static/imgs/double11/swiper/right1.jpg',
				}, {
					left: '../../static/imgs/double11/swiper/left2.jpg',
					middle: '../../static/imgs/double11/swiper/middle2.jpg',
					right: '../../static/imgs/double11/swiper/right2.jpg',
				}],

				singleList1: [{
					sale: "每满100减20",
					title: '车主福利',
					url: '../../static/imgs/double11/single/up/1.jpg',
				}, {
					sale: "每满300减40",
					title: '美妆狂欢',
					url: '../../static/imgs/double11/single/up/2.jpg',
				}, {
					sale: "每满100减20",
					title: '车主福利',
					url: '../../static/imgs/double11/single/up/3.jpg',
				}, {
					sale: "每满300减40",
					title: '美妆狂欢',
					url: '../../static/imgs/double11/single/up/4.jpg',
				}, {
					sale: "每满100减20",
					title: '车主福利',
					url: '../../static/imgs/double11/single/up/5.jpg',
				}, {
					sale: "每满300减40",
					title: '美妆狂欢',
					url: '../../static/imgs/double11/single/up/6.jpg',
				}, {
					sale: "每满100减20",
					title: '车主福利',
					url: '../../static/imgs/double11/single/up/7.jpg',
				}, {
					sale: "每满300减40",
					title: '美妆狂欢',
					url: '../../static/imgs/double11/single/up/8.jpg',
				}],

				singleList2: [{
					sale: "每满100减20",
					title: '车主福利',
					url: '../../static/imgs/double11/single/down/1.jpg',
				}, {
					sale: "每满300减40",
					title: '美妆狂欢',
					url: '../../static/imgs/double11/single/down/2.jpg',
				}, {
					sale: "每满100减20",
					title: '车主福利',
					url: '../../static/imgs/double11/single/down/3.jpg',
				}, {
					sale: "每满300减40",
					title: '美妆狂欢',
					url: '../../static/imgs/double11/single/down/4.jpg',
				}, {
					sale: "每满100减20",
					title: '车主福利',
					url: '../../static/imgs/double11/single/down/5.jpg',
				}, {
					sale: "每满300减40",
					title: '美妆狂欢',
					url: '../../static/imgs/double11/single/down/6.jpg',
				}, {
					sale: "每满100减20",
					title: '车主福利',
					url: '../../static/imgs/double11/single/down/7.jpg',
				}, {
					sale: "每满300减40",
					title: '美妆狂欢',
					url: '../../static/imgs/double11/single/down/8.jpg',
				}],

				// // 图片尺寸变量
				// bgStyle:{
				// 	width:null,
				// 	'--x-offset':null
				// },


				// 东家小院列表
				yardList1: [{
					title: '颜值机箱',
					desc: '特色电脑主机机箱',
					url: [{
						num: 1,
						img: '../../static/imgs/yard/yard_show/1.jpg'
					}, {
						num: 2,
						img: '../../static/imgs/yard/yard_show/2.jpg'
					}]
				}, {
					title: '出游系列',
					desc: '守护你的旅途',
					url: [{
						num: 3,
						img: '../../static/imgs/yard/yard_show/3.jpg'
					}, {
						num: 4,
						img: '../../static/imgs/yard/yard_show/4.jpg'
					}]
				}],

				yardList2: [{
					title: '海囤美妆',
					desc: '护肤首选',
					url: '../../static/imgs/yard/yard_show/5.jpg'
				}, {
					title: '暖心出行',
					desc: '轻暖防寒',
					url: '../../static/imgs/yard/yard_show/6.jpg'
				}, {
					title: '名媛风',
					desc: '你最珍贵',
					url: '../../static/imgs/yard/yard_show/7.jpg'
				}, {
					title: '排汗减肥',
					desc: '轻松减肥',
					url: '../../static/imgs/yard/yard_show/8.jpg'
				}],

				// 每日逛列表
				dailyList: [{
					title: '免息星球',
					text: '白条免息购',
					bg: 'linear-gradient(90deg, #FF2A2A,#F139D2)',
					url: '../../static/imgs/daily_look/look_imgs/1.jpg'
				}, {
					title: '每日特价',
					text: '9块9疯抢',
					bg: 'linear-gradient(90deg, #FE8537,#F02B2B)',
					url: '../../static/imgs/daily_look/look_imgs/2.jpg'
				}, {
					title: '品牌闪购',
					text: '汇大牌好价',
					bg: 'linear-gradient(90deg, #FF765C,#FF23B3)',
					url: '../../static/imgs/daily_look/look_imgs/3.jpg'
				}, {
					title: '京东直播',
					text: '好货即刻买',
					bg: 'linear-gradient(90deg, #FF2A00,#FF00AF)',
					url: '../../static/imgs/daily_look/look_imgs/4.jpg'
				}, {
					title: '排行榜',
					text: '专属购物指南',
					bg: 'linear-gradient(90deg, #D400FF,#FF320A)',
					url: '../../static/imgs/daily_look/look_imgs/5.jpg'
				}, {
					title: '拍拍好物',
					text: 'iPhone 5折起',
					bg: 'linear-gradient(90deg, #00C2AB,#3E94FF)',
					url: '../../static/imgs/daily_look/look_imgs/6.jpg'
				}, {
					title: '新品首发',
					text: '京东小魔方',
					bg: 'linear-gradient(90deg, #FF765C,#FF23B3)',
					url: '../../static/imgs/daily_look/look_imgs/7.jpg'
				}, {
					title: '发现好货',
					text: '教你买买买',
					bg: 'linear-gradient(90deg, #2AD396,#85BB1F)',
					url: '../../static/imgs/daily_look/look_imgs/8.jpg'
				}],

				// 每日推荐列表
				cmList: [{
					title: '克雷士在线式UPS不间断电源C3KVA2400W家用办公电脑稳压机房服务器内置电池应急备用防停电',
					img: '../../static/imgs/commend/cm_list/1.jpg',
					price: '￥1450',
					cmIcon: '../../static/imgs/commend/cm_icon/db11.png',
					cmSort: '../../static/imgs/commend/cm_icon/shop.png',
					cmTag: ''
				}, {
					title: '华硕（ASUS）RT-AX86U双频5700M全千兆路由无线路由器/一键性能手游加速/2.5G端口/WiFi6',
					img: '../../static/imgs/commend/cm_list/2.jpg',
					price: '￥1399',
					cmIcon: '../../static/imgs/commend/cm_icon/db11.png',
					cmSort: '../../static/imgs/commend/cm_icon/wl.png',
					cmTag: '闪购'
				}, {
					title: '上海鑫鼎泰可折叠培训桌椅组合办公书桌课桌椅培训桌长条拼接会议桌移动带轮翻板讨论桌折叠椅',
					img: '../../static/imgs/commend/cm_list/3.jpg',
					price: '￥180',
					cmIcon: '../../static/imgs/commend/cm_icon/db11.png',
					cmSort: '../../static/imgs/commend/cm_icon/zy.png',
					cmTag: ''
				}, {
					title: '飞克（FEIKE）手表男 全自动机械表时尚潮流腕表商务休闲运动夜光防水钢带男表十大品牌 银壳白面黑带',
					img: '../../static/imgs/commend/cm_list/4.jpg',
					price: '￥1079',
					cmIcon: '../../static/imgs/commend/cm_icon/db11.png',
					cmSort: '',
					cmTag: '满减'
				}]
			}
		},

		onLoad() {},
		
		// 监听页面滚动事件
		onPageScroll(e) {
			this.scrollHeight = e.scrollTop
			
			if (this.scrollHeight > 300) {
				this.isShow = true
			} else {
				this.isShow = false
			}
		},
		
		onNavigationBarButtonTap(e) {
			if(e.index === 0){
				uni.switchTab({
				  url: '/pages/sort/sort'
				})
			}else{
				uni.switchTab({
				  url: '/pages/mine/mine'
				})
			}
		},

		methods: {
			// 轮播图
			imgChange(e) {
				// console.log(e)
			},

			// 返回顶部操作
			toTop() {
				uni.pageScrollTo({
					scrollTop: 0
				})
			},

			// 下载的外链
			toPage(url) {
				uni.navigateTo({
					url: url
				})
			},
			
			// 跳转到bar
			toBar(){
				uni.switchTab({
				  url: '/pages/mine/mine'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	page{
		background-color: #f2f2f2;
	}
	
	.container {
		// background-color: rgba(239,101,54,0.7);
		// background-color: rgb(239,101,54);
		overflow: hidden;
		
		// .t_top{
		// 	width: 750upx;
		// 	height: 88upx;
		// 	background-color: rgba(208, 8, 89, 0.7);
		// }

		.head_box {
			position: fixed;
			width: 750upx;
			height: 88upx;
			background-color: rgba(208, 8, 89, 0.7);
			// background-color: red;
			z-index: 2;

			.head_item {
				display: flex;
				position: relative;

				.jd_list,
				.jd_icon,
				.head_split,
				.jd_search,
				.head_search,
				.jd_mine {
					position: absolute;
				}

				.jd_list {
					left: 20upx;
					top: 20upx;
				}

				.jd_icon {
					left: 105upx;
					top: 25upx;
				}

				.head_split {
					width: 2upx;
					height: 36upx;
					background-color: #ccc;
					left: 163upx;
					top: 28upx;
				}

				.jd_search {
					left: 180upx;
					top: 25upx;
				}

				.head_search {
					width: 580upx;
					height: 60upx;
					line-height: 88upx;
					margin-left: 90upx;
					margin-top: 8px;
					text-align: center;
					background-color: #f2f2f2;
					border-radius: 30upx;
					z-index: -1;
					color: #ccc;
				}

				.jd_mine {
					left: 690upx;
					top: 12upx;
				}

			}
		}

		.swiper {
			margin-top: 88upx;
			width: 750upx;
			height: 277upx;
			background-color: rgba(208, 8, 89, 0.7);

			.swiper_box {
				.swiper_item {
					width: 700upx;
					height: 277upx;
					margin-left: 25upx;
				}
			}
		}

		.ads {
			width: 750upx;
			height: 240upx;
			display: flex;

			.ads_left {
				width: 25%;
				height: 100%;
				background: url(../../static/imgs/ads/left.png) no-repeat;
				background-size: cover;

				image {
					margin-left: 35upx;
					margin-top: 50upx;
					width: 120upx;
					height: 140upx;
				}
			}

			.ads_middle {
				width: 50%;
				height: 100%;
				background: url(../../static/imgs/ads/ad.gif) no-repeat;
				background-size: cover;

				.img_first {
					width: 120upx;
					height: 140upx;
					margin-left: 50upx;
					margin-top: 45upx;
				}

				.img_second {
					width: 120upx;
					height: 140upx;
					margin-left: 70upx;
					margin-top: 45upx;
				}
			}

			.ads_right {
				width: 25%;
				height: 100%;
				background: url(../../static/imgs/ads/right.png) no-repeat;
				background-size: cover;

				image {
					margin-left: 35upx;
					margin-top: 50upx;
					width: 120upx;
					height: 140upx;
				}
			}

			.ads_left,
			.ads_right {
				text {
					display: block;
					font-size: 12upx;
					font-family: PingFang;
					font-weight: 500;
					color: #FFFFFF;
					margin-left: 45upx;
					margin-top: -8upx;
				}
			}
		}

		.nav_box {
			width: 750upx;
			height: 340upx;
			// background-color: rgba(203,52,68,0.7);
			// background-color: rgba(255,71,71,0.7);
			background: linear-gradient(39deg, rgba(203, 52, 68, 0.4), rgba(255, 71, 71, 0.5));
			overflow: hidden;

			.nav_item {
				width: 20%;
				float: left;
				margin-top: 30upx;

				image {
					margin: 0 auto;
					display: block;
					width: 80upx;
					height: 80upx;
				}

				text {
					display: block;
					text-align: center;
					color: #fff;
					font-size: 18upx;
					margin-top: 15upx;
				}
			}
		}

		.seckill {
			width: 750upx;
			height: 320upx;
			background-color: rgba(239, 101, 54, 0.7);
			overflow: hidden;

			.kill_box {
				width: 710upx;
				height: 280upx;
				background-color: #fff;
				border-radius: 30upx;
				margin-top: 20upx;
				margin-left: 20upx;
				overflow: hidden;

				.kill_head {
					width: 100%;
					height: 70upx;
					background: url(../../static/imgs/seckill/head_bg.png) no-repeat;
					background-size: cover;
					display: flex;

					.kill_title {
						font-size: 30upx;
						font-family: PingFang;
						color: #333333;
						margin-left: 20upx;
						margin-top: 10upx;
					}

					.kill_clock {
						color: #f23030;
						font-size: 18upx;
						margin-left: 20upx;
						margin-top: 20upx;
					}

					.clock_img {
						width: 41upx;
						height: 35upx;
						margin-top: 18upx;
					}

					.kill_square {
						width: 30upx;
						height: 36upx;
						background: linear-gradient(39deg, #ff6152, #fa2c19);
						margin-top: 10upx;
						border-radius: 8upx;
						color: #fff;
						font-size: 12upx;
						text-align: center;
					}

					.first {
						margin-left: 30upx;
					}

					.quote {
						font-weight: bold;
						margin-top: 15upx;
						color: #f23030;
						font-size: 24upx;
						padding: 0 5upx;

					}

					.kill_more {
						color: #f23030;
						font-size: 18upx;
						margin-left: 210upx;
						margin-top: 20upx;
					}

					.more_img {
						width: 22upx;
						height: 22upx;
						margin-top: 25upx;
						margin-left: 6upx;
					}


				}

				.kill_con {
					width: 16.6%;
					float: left;
					margin-top: 10upx;

					image {
						margin: 0 auto;
						display: block;
						width: 110upx;
						height: 110upx;
					}

					.sale {
						color: #f2270c;
						font-size: 28upx;
						margin-top: 30upx;
						text-align: center;
						margin-left: 15upx;
					}

					.old {
						display: block;
						color: #999;
						font-size: 12upx;
						margin-top: -5upx;
						text-align: center;
						text-decoration: line-through;
					}
				}
			}
		}

		.to_top {
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

		.to_load {
			width: 65upx;
			height: 60upx;
			z-index: 20;
			position: fixed;
			left: 685upx;
			top: 300upx;
			background: rgba(242, 39, 12, 0.9) url(../../static/imgs/toDownload/logo.png) no-repeat;
			background-size: 52upx 52upx;
			background-position: 4upx 4upx;
			border-top-left-radius: 35upx;
			border-bottom-left-radius: 35upx;

			.tips {
				display: none;
				width: 150upx;
				height: 60upx;
				color: #fff;
				font-size: 24upx;
				text-align: center;
				line-height: 60upx;
			}

			&:hover {
				width: 240upx;
				left: 510upx;

				.tips {
					display: block;
					margin-left: 77.5upx;
				}
			}
		}

		.freshmen {
			width: 750upx;
			height: 240upx;
			background-color: rgba(239, 101, 54, 0.7);
			display: flex;
			padding: 0 20upx;

			.fh_item {
				image {
					width: 355upx;
					height: 240upx;
				}
			}
		}

		.fh_con {
			width: 750upx;
			height: 365upx;
			background-color: rgba(239, 101, 54, 0.7);
			// margin-top: 15upx;
			padding: 0 5upx;
			overflow: hidden;

			image {
				width: 740upx;
				height: 100upx;
				margin-top: 15upx;
			}


			.fh_show {
				width: 750upx;
				height: 242upx;
				overflow: hidden;
				padding: 0 10upx;
				margin-top: -8upx;

				.show_item {
					width: 175upx;
					height: 242upx;
					float: left;
					background-size: cover;
					background-repeat: no-repeat;
					margin-right: 5upx;

					image {
						width: 130upx;
						height: 130upx;
						margin-left: 25upx;
						margin-top: 19upx;
					}

					.title {
						display: block;
						text-align: center;
						font-size: 28upx;
						margin: 10upx auto 0;
					}

					.desc {
						display: block;
						text-align: center;
						font-size: 24upx;
						margin: 0 auto;
					}
				}
			}
		}

		.choice_box {
			// margin-top: 16upx;
			width: 750upx;
			height: 740upx;
			background-color: rgba(239, 101, 54, 0.7);

			image {
				width: 610upx;
				height: 60upx;
				margin-left: 70upx;
				margin-top: 16upx;
			}

			.single_box {
				margin-top: 10upx;
				width: 1440upx;
				height: 200upx;
				overflow: hidden;
				margin-left: 5upx;
				position: relative;

				.single_swiper {
					position: absolute;
					left: 0;
					top: 0;
					width: 100%;
					animation: 16s move infinite linear;
					// animation-fill-mode: forwards;


					.single_show {
						width: 180upx;
						float: left;

						.single_item {
							background-size: cover;

							text {
								display: block;
								text-align: center;
								margin: 10upx auto;
							}

						}
					}
				}

				@keyframes move {
					// 0% {
					// 	left: 0;
					// }

					// 100% {
					// 	left: -1440upx;
					// }

					from {
						transform: translateX(0px);
					}
					to {
						transform: translateX(-1440upx);
					}
				}
			}

			.all_box {
				margin-top: 15upx;
				width: 750upx;
				height: 200upx;

				.all_item {
					margin-left: -50upx;
					margin-bottom: 20upx;

					.all_left,
					.all_right {
						display: inline-block;
						width: 210upx;
						height: 165upx;
						margin-right: -55upx;
					}

					.all_middle {
						display: inline-block;
						width: 260upx;
						height: 195upx;
						margin-right: -55upx;
					}
				}
			}
		}

		.yard {
			overflow: hidden;

			.yard_bg {
				width: 750upx;
				height: 70upx;
			}

			.yard_box {
				width: 714upx;
				height: 242upx;
				margin-left: 18upx;
				margin-top: -10upx;
				overflow: hidden;

				.yard_item {
					width: 355upx;
					height: 100%;
					float: left;
					background-color: #fff;
					position: relative;
					margin-right: 2upx;

					.yard_title,
					.yard_desc,
					.img_box {
						position: absolute;
					}

					.yard_title {
						background: -webkit-linear-gradient(90deg, #45CAFF, #1471FB);
						-webkit-background-clip: text;
						-webkit-text-fill-color: transparent;
						font-size: 32upx;
						font-weight: bold;
						left: 10upx;
						top: 10upx;
					}

					.yard_desc {
						color: #666771;
						font-size: 24upx;
						left: 10upx;
						top: 50upx;
					}

					.yard_show {
						width: 355upx;
						overflow: hidden;

						.img_box {
							width: 160upx;
							height: 160upx;
							float: left;
							position: relative;
							margin-top: 100upx;
							margin-left: 15upx;

							image {
								position: absolute;
								margin: 20 auto;
								width: 120upx;
								height: 120upx;
							}
						}
					}



				}
			}

			.yard_list {
				width: 714upx;
				height: 242upx;
				margin-left: 18upx;
				margin-top: 2upx;
				overflow: hidden;

				.yard_single {
					width: 177upx;
					height: 100%;
					background-color: #fff;
					float: left;
					margin-right: 2upx;
					position: relative;

					.title,
					.desc,
					image {
						position: absolute;
					}

					.title {
						font-size: 32upx;
						font-weight: bold;
						color: rgb(0, 0, 0);
						top: 15upx;
						left: 20upx;
					}

					.desc {
						color: #666771;
						font-size: 24upx;
						left: 20upx;
						top: 55upx;
					}

					image {
						width: 120upx;
						height: 120upx;
						left: 28.5upx;
						top: 100upx;
					}
				}
			}

		}

		.daily_look {
			width: 710upx;
			height: 548upx;
			margin-top: 20upx;
			margin-left: 20upx;
			overflow: hidden;

			image {
				width: 750upx;
				height: 70upx;
				margin-bottom: -8upx;
			}

			.look_box {
				width: 175upx;
				height: 240upx;
				margin-right: 2upx;
				background-color: #fff;
				float: left;
				position: relative;
				margin-top: 2upx;

				.look_title,
				.look_desc,
				image {
					position: absolute;
				}

				.look_title {
					-webkit-background-clip: text;
					-webkit-text-fill-color: transparent;
					font-size: 34upx;
					left: 20upx;
					top: 10upx;
				}

				.look_desc {
					color: #222222;
					font-size: 24upx;
					left: 20upx;
					top: 55upx;
				}

				image {
					width: 120upx;
					height: 120upx;
					left: 27.5upx;
					top: 100upx;
				}
			}

		}

		.cm_box {
			margin-top: 30upx;
			width: 750upx;
			overflow: hidden;

			image {
				width: 750upx;
				height: 70upx;
			}

			.cm_item {
				width: 346upx;
				height: 486upx;
				float: left;
				background-color: #fff;
				border-radius: 15px;
				margin-left: 18upx;
				margin-bottom: 20upx;
				position: relative;

				&:nth-child(2n+1) {
					margin-left: 18upx;
				}

				.item,
				.icon,
				.cm_title,
				.cm_price,
				.cm_btn {
					position: absolute;
				}

				.item {
					width: 346upx;
					height: 346upx;
					border-top-left-radius: 15px;
					border-top-right-radius: 15px;
				}

				.icon {
					width: 39upx;
					height: 26upx;
					left: 15upx;
					top: 370upx;
				}

				.cm_title {
					color: #1a1a1a;
					font-size: 26upx;
					top: 360upx;
					line-height: 26upx;
					left: 65upx;
				}

				.cm_price {
					top: 420upx;
					color: #fa2c19;
					font-family: JDZhengHT-EN-Regular;
					left: 10upx;
				}

				.cm_btn {
					width: 92upx;
					height: 44upx;
					color: grey;
					background-color: #f0f2f5;
					border-top-left-radius: 15upx;
					border-bottom-left-radius: 15upx;
					text-align: center;
					line-height: 44upx;
					font-size: 22upx;
					left: 260upx;
					top: 425upx;
				}
			}
		}


		// 大框框
		.bigBox {
			width: 180upx;
			height: 200upx;
			font-size: 20upx;
		}

		// 小框框
		.smallBox {
			width: 152upx;
			height: 170upx;
			margin: 15upx auto;
			font-size: 10upx;
		}

		// 小背景1
		.min1 {
			color: rgb(120, 66, 242);
			background: url(../../static/imgs/double11/single/min1.png) no-repeat;
		}

		// 小背景2
		.min2 {
			color: rgb(243, 45, 70);
			background: url(../../static/imgs/double11/single/min2.png) no-repeat;
		}

		.min1,
		.min2 {
			overflow: hidden;

			image {
				display: block;
				margin: 15upx auto;
				width: 130upx;
				height: 130upx;
				z-index: -1;
				border-radius: 20upx;
				margin-bottom: -15upx;
			}
		}

		// 大背景1
		.big1 {
			color: rgb(248, 89, 26);
			background: url(../../static/imgs/double11/single/big1.png) no-repeat;
		}

		// 大背景2
		.big2 {
			color: rgb(255, 0, 175);
			background: url(../../static/imgs/double11/single/big2.png) no-repeat;
		}

		.big1,
		.big2 {
			overflow: hidden;

			image {
				display: block;
				margin: 15upx auto;
				width: 155upx;
				height: 155upx;
				z-index: -1;
				border-radius: 20upx;
				margin-bottom: -15upx;
			}
		}
	}
</style>
