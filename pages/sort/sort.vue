<template>
	<view class="container">
		<view class="t_top"></view>
		
		<!-- 头部 -->
	<!-- 	<view class="head">
			<view class="back">
				<image src="../../static/back.png" mode="" @click="toBar"></image>
			</view>
			
			<view class="search">
				<view class="search_icon"></view>
				<input class="search_ipt" placeholder="请输入搜索内容">
			</view>
		</view> -->
	
		<!-- 分类盒子 -->
		<view class="sort_box">
			<view class="left">
				<!-- 第一种方法，和右边一样，使用锚点定位 -->
				<scroll-view scroll-y="true" style="white-space: nowrap;height: 1144upx;" :scroll-into-view="clickId">
					<view class="nav_item" v-for="(item,index) in itemList" :id="'po' + index" :key="index" @click="setId(index)">
						{{item.title}}
					</view>
				</scroll-view>
				
				<!-- 第二种方法，用transform的translateY，但要做一个判断(problem) -->
				<!-- <scroll-view scroll-y="true" style="white-space: nowrap;height: 1290upx;position: relative;" :style="itemList.length - num  >  13 ? `transform: translateY(-${num*90}upx);` : `transform: translateY(-0upx);`">
					<view class="nav_item" v-for="(item,index) in itemList" :key="index" @click="setId(index)">
						{{item.title}}
					</view>
				</scroll-view> -->
				
				
				
			</view>
			
			<view class="right">
				<scroll-view scroll-y="true" style="white-space: nowrap;height: 1290upx;" :scroll-into-view="clickId">
					<view class="nav_box" v-for="(item,index) in itemList" :key="index">
						<view class="title">
							<text class="nav_title" :id="'po' + index">{{item.title}}</text>
							<view class="rank_box">
								<image src="../../static/imgs/sort/rank.png" mode="" class="rank_icon"></image>
								<text>排行榜</text>
								<image src="../../static/imgs/sort/right-arrow.png" mode="" class="right_arrow"></image>
							</view>
						</view>
						
						<view class="item_list">
							<view class="item_box" v-for="(v,k) in item.list" :key="k">
								<image :src=v.url mode=""></image>
								<text>{{v.title}}</text>
							</view>
						</view>
					</view>
				</scroll-view>
			</view>
			
		</view>
	
		
	</view>
</template>

<script>
	export default{
		data(){
			return{
				itemList:[{
					title:'热门推荐',
					list:[{
						title:'空调',
						url:'../../static/imgs/sort/sort-list/1.jpg'
					}]
				},{
					title:'手机数码',
					list:[{
						title:'冰箱',
						url:'../../static/imgs/sort/sort-list/2.jpg'
					}]
				},{
					title:'电脑办公',
					list:[{
						title:'空调',
						url:'../../static/imgs/sort/sort-list/1.jpg'
					},{
						title:'冰箱',
						url:'../../static/imgs/sort/sort-list/2.jpg'
					},{
						title:'电视',
						url:'../../static/imgs/sort/sort-list/3.png'
					},{
						title:'手机',
						url:'../../static/imgs/sort/sort-list/4.png'
					},{
						title:'全面屏手机',
						url:'../../static/imgs/sort/sort-list/5.jpg'
					},{
						title:'游戏手机',
						url:'../../static/imgs/sort/sort-list/6.jpg'
					},{
						title:'保健品',
						url:'../../static/imgs/sort/sort-list/7.jpg'
					},{
						title:'口罩',
						url:'../../static/imgs/sort/sort-list/8.jpg'
					},{
						title:'驱蚊用品',
						url:'../../static/imgs/sort/sort-list/9.jpg'
					},{
						title:'电磁炉',
						url:'../../static/imgs/sort/sort-list/10.jpg'
					},{
						title:'电热水壶',
						url:'../../static/imgs/sort/sort-list/11.jpg'
					},{
						title:'数据线',
						url:'../../static/imgs/sort/sort-list/12.jpg'
					},{
						title:'图书',
						url:'../../static/imgs/sort/sort-list/13.jpg'
					},{
						title:'美妆护肤',
						url:'../../static/imgs/sort/sort-list/14.jpg'
					},{
						title:'除菌液',
						url:'../../static/imgs/sort/sort-list/15.jpg'
					}]
				},{
					title:'家用电器',
					list:[{
						title:'空调',
						url:'../../static/imgs/sort/sort-list/1.jpg'
					},{
						title:'冰箱',
						url:'../../static/imgs/sort/sort-list/2.jpg'
					},{
						title:'电视',
						url:'../../static/imgs/sort/sort-list/3.png'
					},{
						title:'手机',
						url:'../../static/imgs/sort/sort-list/4.png'
					},{
						title:'全面屏手机',
						url:'../../static/imgs/sort/sort-list/5.jpg'
					},{
						title:'游戏手机',
						url:'../../static/imgs/sort/sort-list/6.jpg'
					},{
						title:'保健品',
						url:'../../static/imgs/sort/sort-list/7.jpg'
					},{
						title:'口罩',
						url:'../../static/imgs/sort/sort-list/8.jpg'
					},{
						title:'驱蚊用品',
						url:'../../static/imgs/sort/sort-list/9.jpg'
					},{
						title:'电磁炉',
						url:'../../static/imgs/sort/sort-list/10.jpg'
					},{
						title:'电热水壶',
						url:'../../static/imgs/sort/sort-list/11.jpg'
					},{
						title:'数据线',
						url:'../../static/imgs/sort/sort-list/12.jpg'
					},{
						title:'图书',
						url:'../../static/imgs/sort/sort-list/13.jpg'
					},{
						title:'美妆护肤',
						url:'../../static/imgs/sort/sort-list/14.jpg'
					},{
						title:'除菌液',
						url:'../../static/imgs/sort/sort-list/15.jpg'
					}]
				},{
					title:'美妆护肤',
					list:[{
						title:'空调',
						url:'../../static/imgs/sort/sort-list/1.jpg'
					},{
						title:'冰箱',
						url:'../../static/imgs/sort/sort-list/2.jpg'
					},{
						title:'电视',
						url:'../../static/imgs/sort/sort-list/3.png'
					},{
						title:'手机',
						url:'../../static/imgs/sort/sort-list/4.png'
					},{
						title:'全面屏手机',
						url:'../../static/imgs/sort/sort-list/5.jpg'
					},{
						title:'游戏手机',
						url:'../../static/imgs/sort/sort-list/6.jpg'
					},{
						title:'保健品',
						url:'../../static/imgs/sort/sort-list/7.jpg'
					},{
						title:'口罩',
						url:'../../static/imgs/sort/sort-list/8.jpg'
					},{
						title:'驱蚊用品',
						url:'../../static/imgs/sort/sort-list/9.jpg'
					},{
						title:'电磁炉',
						url:'../../static/imgs/sort/sort-list/10.jpg'
					},{
						title:'电热水壶',
						url:'../../static/imgs/sort/sort-list/11.jpg'
					},{
						title:'数据线',
						url:'../../static/imgs/sort/sort-list/12.jpg'
					},{
						title:'图书',
						url:'../../static/imgs/sort/sort-list/13.jpg'
					},{
						title:'美妆护肤',
						url:'../../static/imgs/sort/sort-list/14.jpg'
					},{
						title:'除菌液',
						url:'../../static/imgs/sort/sort-list/15.jpg'
					}]
				},{
					title:'个护清洁',
					list:[{
						title:'空调',
						url:'../../static/imgs/sort/sort-list/1.jpg'
					},{
						title:'冰箱',
						url:'../../static/imgs/sort/sort-list/2.jpg'
					},{
						title:'电视',
						url:'../../static/imgs/sort/sort-list/3.png'
					},{
						title:'手机',
						url:'../../static/imgs/sort/sort-list/4.png'
					},{
						title:'全面屏手机',
						url:'../../static/imgs/sort/sort-list/5.jpg'
					},{
						title:'游戏手机',
						url:'../../static/imgs/sort/sort-list/6.jpg'
					},{
						title:'保健品',
						url:'../../static/imgs/sort/sort-list/7.jpg'
					},{
						title:'口罩',
						url:'../../static/imgs/sort/sort-list/8.jpg'
					},{
						title:'驱蚊用品',
						url:'../../static/imgs/sort/sort-list/9.jpg'
					},{
						title:'电磁炉',
						url:'../../static/imgs/sort/sort-list/10.jpg'
					},{
						title:'电热水壶',
						url:'../../static/imgs/sort/sort-list/11.jpg'
					},{
						title:'数据线',
						url:'../../static/imgs/sort/sort-list/12.jpg'
					},{
						title:'图书',
						url:'../../static/imgs/sort/sort-list/13.jpg'
					},{
						title:'美妆护肤',
						url:'../../static/imgs/sort/sort-list/14.jpg'
					},{
						title:'除菌液',
						url:'../../static/imgs/sort/sort-list/15.jpg'
					}]
				},{
					title:'京东超市',
					list:[{
						title:'空调',
						url:'../../static/imgs/sort/sort-list/1.jpg'
					},{
						title:'冰箱',
						url:'../../static/imgs/sort/sort-list/2.jpg'
					},{
						title:'电视',
						url:'../../static/imgs/sort/sort-list/3.png'
					},{
						title:'手机',
						url:'../../static/imgs/sort/sort-list/4.png'
					},{
						title:'全面屏手机',
						url:'../../static/imgs/sort/sort-list/5.jpg'
					},{
						title:'游戏手机',
						url:'../../static/imgs/sort/sort-list/6.jpg'
					},{
						title:'保健品',
						url:'../../static/imgs/sort/sort-list/7.jpg'
					},{
						title:'口罩',
						url:'../../static/imgs/sort/sort-list/8.jpg'
					},{
						title:'驱蚊用品',
						url:'../../static/imgs/sort/sort-list/9.jpg'
					},{
						title:'电磁炉',
						url:'../../static/imgs/sort/sort-list/10.jpg'
					},{
						title:'电热水壶',
						url:'../../static/imgs/sort/sort-list/11.jpg'
					},{
						title:'数据线',
						url:'../../static/imgs/sort/sort-list/12.jpg'
					},{
						title:'图书',
						url:'../../static/imgs/sort/sort-list/13.jpg'
					},{
						title:'美妆护肤',
						url:'../../static/imgs/sort/sort-list/14.jpg'
					},{
						title:'除菌液',
						url:'../../static/imgs/sort/sort-list/15.jpg'
					}]
				},{
					title:'男装',
					list:[{
						title:'空调',
						url:'../../static/imgs/sort/sort-list/1.jpg'
					},{
						title:'冰箱',
						url:'../../static/imgs/sort/sort-list/2.jpg'
					},{
						title:'电视',
						url:'../../static/imgs/sort/sort-list/3.png'
					},{
						title:'手机',
						url:'../../static/imgs/sort/sort-list/4.png'
					},{
						title:'全面屏手机',
						url:'../../static/imgs/sort/sort-list/5.jpg'
					},{
						title:'游戏手机',
						url:'../../static/imgs/sort/sort-list/6.jpg'
					},{
						title:'保健品',
						url:'../../static/imgs/sort/sort-list/7.jpg'
					},{
						title:'口罩',
						url:'../../static/imgs/sort/sort-list/8.jpg'
					},{
						title:'驱蚊用品',
						url:'../../static/imgs/sort/sort-list/9.jpg'
					},{
						title:'电磁炉',
						url:'../../static/imgs/sort/sort-list/10.jpg'
					},{
						title:'电热水壶',
						url:'../../static/imgs/sort/sort-list/11.jpg'
					},{
						title:'数据线',
						url:'../../static/imgs/sort/sort-list/12.jpg'
					},{
						title:'图书',
						url:'../../static/imgs/sort/sort-list/13.jpg'
					},{
						title:'美妆护肤',
						url:'../../static/imgs/sort/sort-list/14.jpg'
					},{
						title:'除菌液',
						url:'../../static/imgs/sort/sort-list/15.jpg'
					}]
				},{
					title:'女装',
					list:[{
						title:'空调',
						url:'../../static/imgs/sort/sort-list/1.jpg'
					},{
						title:'冰箱',
						url:'../../static/imgs/sort/sort-list/2.jpg'
					},{
						title:'电视',
						url:'../../static/imgs/sort/sort-list/3.png'
					},{
						title:'手机',
						url:'../../static/imgs/sort/sort-list/4.png'
					},{
						title:'全面屏手机',
						url:'../../static/imgs/sort/sort-list/5.jpg'
					},{
						title:'游戏手机',
						url:'../../static/imgs/sort/sort-list/6.jpg'
					},{
						title:'保健品',
						url:'../../static/imgs/sort/sort-list/7.jpg'
					},{
						title:'口罩',
						url:'../../static/imgs/sort/sort-list/8.jpg'
					},{
						title:'驱蚊用品',
						url:'../../static/imgs/sort/sort-list/9.jpg'
					},{
						title:'电磁炉',
						url:'../../static/imgs/sort/sort-list/10.jpg'
					},{
						title:'电热水壶',
						url:'../../static/imgs/sort/sort-list/11.jpg'
					},{
						title:'数据线',
						url:'../../static/imgs/sort/sort-list/12.jpg'
					},{
						title:'图书',
						url:'../../static/imgs/sort/sort-list/13.jpg'
					},{
						title:'美妆护肤',
						url:'../../static/imgs/sort/sort-list/14.jpg'
					},{
						title:'除菌液',
						url:'../../static/imgs/sort/sort-list/15.jpg'
					}]
				},{
					title:'男鞋',
					list:[{
						title:'空调',
						url:'../../static/imgs/sort/sort-list/1.jpg'
					},{
						title:'冰箱',
						url:'../../static/imgs/sort/sort-list/2.jpg'
					},{
						title:'电视',
						url:'../../static/imgs/sort/sort-list/3.png'
					},{
						title:'手机',
						url:'../../static/imgs/sort/sort-list/4.png'
					},{
						title:'全面屏手机',
						url:'../../static/imgs/sort/sort-list/5.jpg'
					},{
						title:'游戏手机',
						url:'../../static/imgs/sort/sort-list/6.jpg'
					},{
						title:'保健品',
						url:'../../static/imgs/sort/sort-list/7.jpg'
					},{
						title:'口罩',
						url:'../../static/imgs/sort/sort-list/8.jpg'
					},{
						title:'驱蚊用品',
						url:'../../static/imgs/sort/sort-list/9.jpg'
					},{
						title:'电磁炉',
						url:'../../static/imgs/sort/sort-list/10.jpg'
					},{
						title:'电热水壶',
						url:'../../static/imgs/sort/sort-list/11.jpg'
					},{
						title:'数据线',
						url:'../../static/imgs/sort/sort-list/12.jpg'
					},{
						title:'图书',
						url:'../../static/imgs/sort/sort-list/13.jpg'
					},{
						title:'美妆护肤',
						url:'../../static/imgs/sort/sort-list/14.jpg'
					},{
						title:'除菌液',
						url:'../../static/imgs/sort/sort-list/15.jpg'
					}]
				},{
					title:'女鞋',
					list:[{
						title:'空调',
						url:'../../static/imgs/sort/sort-list/1.jpg'
					},{
						title:'冰箱',
						url:'../../static/imgs/sort/sort-list/2.jpg'
					},{
						title:'电视',
						url:'../../static/imgs/sort/sort-list/3.png'
					},{
						title:'手机',
						url:'../../static/imgs/sort/sort-list/4.png'
					},{
						title:'全面屏手机',
						url:'../../static/imgs/sort/sort-list/5.jpg'
					},{
						title:'游戏手机',
						url:'../../static/imgs/sort/sort-list/6.jpg'
					},{
						title:'保健品',
						url:'../../static/imgs/sort/sort-list/7.jpg'
					},{
						title:'口罩',
						url:'../../static/imgs/sort/sort-list/8.jpg'
					},{
						title:'驱蚊用品',
						url:'../../static/imgs/sort/sort-list/9.jpg'
					},{
						title:'电磁炉',
						url:'../../static/imgs/sort/sort-list/10.jpg'
					},{
						title:'电热水壶',
						url:'../../static/imgs/sort/sort-list/11.jpg'
					},{
						title:'数据线',
						url:'../../static/imgs/sort/sort-list/12.jpg'
					},{
						title:'图书',
						url:'../../static/imgs/sort/sort-list/13.jpg'
					},{
						title:'美妆护肤',
						url:'../../static/imgs/sort/sort-list/14.jpg'
					},{
						title:'除菌液',
						url:'../../static/imgs/sort/sort-list/15.jpg'
					}]
				},{
					title:'母婴童装',
					list:[{
						title:'空调',
						url:'../../static/imgs/sort/sort-list/1.jpg'
					},{
						title:'冰箱',
						url:'../../static/imgs/sort/sort-list/2.jpg'
					},{
						title:'电视',
						url:'../../static/imgs/sort/sort-list/3.png'
					},{
						title:'手机',
						url:'../../static/imgs/sort/sort-list/4.png'
					},{
						title:'全面屏手机',
						url:'../../static/imgs/sort/sort-list/5.jpg'
					},{
						title:'游戏手机',
						url:'../../static/imgs/sort/sort-list/6.jpg'
					},{
						title:'保健品',
						url:'../../static/imgs/sort/sort-list/7.jpg'
					},{
						title:'口罩',
						url:'../../static/imgs/sort/sort-list/8.jpg'
					},{
						title:'驱蚊用品',
						url:'../../static/imgs/sort/sort-list/9.jpg'
					},{
						title:'电磁炉',
						url:'../../static/imgs/sort/sort-list/10.jpg'
					},{
						title:'电热水壶',
						url:'../../static/imgs/sort/sort-list/11.jpg'
					},{
						title:'数据线',
						url:'../../static/imgs/sort/sort-list/12.jpg'
					},{
						title:'图书',
						url:'../../static/imgs/sort/sort-list/13.jpg'
					},{
						title:'美妆护肤',
						url:'../../static/imgs/sort/sort-list/14.jpg'
					},{
						title:'除菌液',
						url:'../../static/imgs/sort/sort-list/15.jpg'
					}]
				},{
					title:'图书音像',
					list:[{
						title:'空调',
						url:'../../static/imgs/sort/sort-list/1.jpg'
					},{
						title:'冰箱',
						url:'../../static/imgs/sort/sort-list/2.jpg'
					},{
						title:'电视',
						url:'../../static/imgs/sort/sort-list/3.png'
					},{
						title:'手机',
						url:'../../static/imgs/sort/sort-list/4.png'
					},{
						title:'全面屏手机',
						url:'../../static/imgs/sort/sort-list/5.jpg'
					},{
						title:'游戏手机',
						url:'../../static/imgs/sort/sort-list/6.jpg'
					},{
						title:'保健品',
						url:'../../static/imgs/sort/sort-list/7.jpg'
					},{
						title:'口罩',
						url:'../../static/imgs/sort/sort-list/8.jpg'
					},{
						title:'驱蚊用品',
						url:'../../static/imgs/sort/sort-list/9.jpg'
					},{
						title:'电磁炉',
						url:'../../static/imgs/sort/sort-list/10.jpg'
					},{
						title:'电热水壶',
						url:'../../static/imgs/sort/sort-list/11.jpg'
					},{
						title:'数据线',
						url:'../../static/imgs/sort/sort-list/12.jpg'
					},{
						title:'图书',
						url:'../../static/imgs/sort/sort-list/13.jpg'
					},{
						title:'美妆护肤',
						url:'../../static/imgs/sort/sort-list/14.jpg'
					},{
						title:'除菌液',
						url:'../../static/imgs/sort/sort-list/15.jpg'
					}]
				},{
					title:'运动户外',
					list:[{
						title:'空调',
						url:'../../static/imgs/sort/sort-list/1.jpg'
					},{
						title:'冰箱',
						url:'../../static/imgs/sort/sort-list/2.jpg'
					},{
						title:'电视',
						url:'../../static/imgs/sort/sort-list/3.png'
					},{
						title:'手机',
						url:'../../static/imgs/sort/sort-list/4.png'
					},{
						title:'全面屏手机',
						url:'../../static/imgs/sort/sort-list/5.jpg'
					},{
						title:'游戏手机',
						url:'../../static/imgs/sort/sort-list/6.jpg'
					},{
						title:'保健品',
						url:'../../static/imgs/sort/sort-list/7.jpg'
					},{
						title:'口罩',
						url:'../../static/imgs/sort/sort-list/8.jpg'
					},{
						title:'驱蚊用品',
						url:'../../static/imgs/sort/sort-list/9.jpg'
					},{
						title:'电磁炉',
						url:'../../static/imgs/sort/sort-list/10.jpg'
					},{
						title:'电热水壶',
						url:'../../static/imgs/sort/sort-list/11.jpg'
					},{
						title:'数据线',
						url:'../../static/imgs/sort/sort-list/12.jpg'
					},{
						title:'图书',
						url:'../../static/imgs/sort/sort-list/13.jpg'
					},{
						title:'美妆护肤',
						url:'../../static/imgs/sort/sort-list/14.jpg'
					},{
						title:'除菌液',
						url:'../../static/imgs/sort/sort-list/15.jpg'
					}]
				},{
					title:'内衣服饰',
					list:[{
						title:'空调',
						url:'../../static/imgs/sort/sort-list/1.jpg'
					},{
						title:'冰箱',
						url:'../../static/imgs/sort/sort-list/2.jpg'
					},{
						title:'电视',
						url:'../../static/imgs/sort/sort-list/3.png'
					},{
						title:'手机',
						url:'../../static/imgs/sort/sort-list/4.png'
					},{
						title:'全面屏手机',
						url:'../../static/imgs/sort/sort-list/5.jpg'
					},{
						title:'游戏手机',
						url:'../../static/imgs/sort/sort-list/6.jpg'
					},{
						title:'保健品',
						url:'../../static/imgs/sort/sort-list/7.jpg'
					},{
						title:'口罩',
						url:'../../static/imgs/sort/sort-list/8.jpg'
					},{
						title:'驱蚊用品',
						url:'../../static/imgs/sort/sort-list/9.jpg'
					},{
						title:'电磁炉',
						url:'../../static/imgs/sort/sort-list/10.jpg'
					},{
						title:'电热水壶',
						url:'../../static/imgs/sort/sort-list/11.jpg'
					},{
						title:'数据线',
						url:'../../static/imgs/sort/sort-list/12.jpg'
					},{
						title:'图书',
						url:'../../static/imgs/sort/sort-list/13.jpg'
					},{
						title:'美妆护肤',
						url:'../../static/imgs/sort/sort-list/14.jpg'
					},{
						title:'除菌液',
						url:'../../static/imgs/sort/sort-list/15.jpg'
					}]
				},{
					title:'食品生鲜',
					list:[{
						title:'空调',
						url:'../../static/imgs/sort/sort-list/1.jpg'
					},{
						title:'冰箱',
						url:'../../static/imgs/sort/sort-list/2.jpg'
					},{
						title:'电视',
						url:'../../static/imgs/sort/sort-list/3.png'
					},{
						title:'手机',
						url:'../../static/imgs/sort/sort-list/4.png'
					},{
						title:'全面屏手机',
						url:'../../static/imgs/sort/sort-list/5.jpg'
					},{
						title:'游戏手机',
						url:'../../static/imgs/sort/sort-list/6.jpg'
					},{
						title:'保健品',
						url:'../../static/imgs/sort/sort-list/7.jpg'
					},{
						title:'口罩',
						url:'../../static/imgs/sort/sort-list/8.jpg'
					},{
						title:'驱蚊用品',
						url:'../../static/imgs/sort/sort-list/9.jpg'
					},{
						title:'电磁炉',
						url:'../../static/imgs/sort/sort-list/10.jpg'
					},{
						title:'电热水壶',
						url:'../../static/imgs/sort/sort-list/11.jpg'
					},{
						title:'数据线',
						url:'../../static/imgs/sort/sort-list/12.jpg'
					},{
						title:'图书',
						url:'../../static/imgs/sort/sort-list/13.jpg'
					},{
						title:'美妆护肤',
						url:'../../static/imgs/sort/sort-list/14.jpg'
					},{
						title:'除菌液',
						url:'../../static/imgs/sort/sort-list/15.jpg'
					}]
				},{
					title:'酒水饮料',
					list:[{
						title:'空调',
						url:'../../static/imgs/sort/sort-list/1.jpg'
					},{
						title:'冰箱',
						url:'../../static/imgs/sort/sort-list/2.jpg'
					},{
						title:'电视',
						url:'../../static/imgs/sort/sort-list/3.png'
					},{
						title:'手机',
						url:'../../static/imgs/sort/sort-list/4.png'
					},{
						title:'全面屏手机',
						url:'../../static/imgs/sort/sort-list/5.jpg'
					},{
						title:'游戏手机',
						url:'../../static/imgs/sort/sort-list/6.jpg'
					},{
						title:'保健品',
						url:'../../static/imgs/sort/sort-list/7.jpg'
					},{
						title:'口罩',
						url:'../../static/imgs/sort/sort-list/8.jpg'
					},{
						title:'驱蚊用品',
						url:'../../static/imgs/sort/sort-list/9.jpg'
					},{
						title:'电磁炉',
						url:'../../static/imgs/sort/sort-list/10.jpg'
					},{
						title:'电热水壶',
						url:'../../static/imgs/sort/sort-list/11.jpg'
					},{
						title:'数据线',
						url:'../../static/imgs/sort/sort-list/12.jpg'
					},{
						title:'图书',
						url:'../../static/imgs/sort/sort-list/13.jpg'
					},{
						title:'美妆护肤',
						url:'../../static/imgs/sort/sort-list/14.jpg'
					},{
						title:'除菌液',
						url:'../../static/imgs/sort/sort-list/15.jpg'
					}]
				}],
				
				
				// 记录点击的id
				clickId:'',
				num:0
			}
		},
		
		// 自定义导航栏的点击事件
		onNavigationBarButtonTap(e) {
			if(e.index === 0){
				uni.switchTab({
				  url: '/pages/index/index'
				})
			}
		},
		
		methods:{
			setId(index){
				console.log(index)
				this.clickId = "po" + index
				this.num = index	
			},
			
			// 返回首页
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
		
		
		// .head{
		// 	width: 750upx;
		// 	height: 88upx;
		// 	background-color: #fff;
		// 	display: flex;
		// 	align-items: center;
			
		// 	.back{
		// 		image{
		// 			width: 40upx;
		// 			height: 40upx;
		// 		}
		// 	}
		
		// 	.search{
		// 		width: 600upx;
		// 		height: 60upx;
		// 		display: flex;
		// 		align-items: center;
		// 		background-color: #f7f7f7;
		// 		border-radius: 30upx;
		// 		margin-left: 20upx;
				
		// 		.search_icon{
		// 			margin-left: 60upx;
		// 			width: 30upx;
		// 			height: 30upx;
		// 			background: url(../../static/search.png) no-repeat;
		// 			background-size: cover;
		// 		}
				
		// 		.search_ipt{
		// 			margin-left: 20upx;
		// 			width: 480upx;
		// 			height: 40upx;
		// 			color: #232326;
		// 			font-size: 28upx;
		// 		}
		// 	}
		// }
		
		.sort_box{
			margin-top: 5upx;
			display: flex;
			
			.left{
				width: 180upx;
				background-color: #f7f7f7;
				overflow: hidden;
				
				.nav_item{
					float: left;
					width: 170upx;
					height: 90upx;
					display: block;
					// border: 1px solid red;
					font-size: 28upx;
					line-height: 90upx;
					text-align: center;
					
					&:hover{
						width: 180upx;
						color: #e93b3d;
						background-color: #fff;
						border-radius: 5upx;
					}
				}
			}
			
			.right{
				width: 568upx;
				background-color: #fff;
				
				.nav_box{
					height: 1144upx;
					
					.title{
						height: 90upx;
						display: flex;
						align-items: center;
						
						.nav_title{
							color: #333;
							font-size: 28upx;
							font-weight: 700;
							line-height: 90upx;
							padding-left: 10upx;
						}
						
						.rank_box{
							display: flex;
							align-items: center;
							margin-left: 310upx;
							
							.rank_icon,.right_arrow{
								width: 24upx;
								height: 24upx;
							}
							
							text{
								color: #252525;
								font-size: 24upx;
							}
						}
						
						
					}
					
					.item_list{
						width: 100%;
						height: 100%;
						overflow: hidden;
						
						.item_box{
							width: 33.33%;
							float: left;
							text-align: center;
							
							image{
								display: block;
								width: 140upx;
								height: 140upx;
								margin: 0 auto;
							}
							
							text{
								color: #252525;
								font-size: 24upx;
							}
						}
					}
				}
			}
		
		}
	
	}
</style>