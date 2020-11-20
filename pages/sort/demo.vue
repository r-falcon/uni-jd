<template>
	<view class="container">
		<view class="col_box">
			<view class="left">
				<scroll-view scroll-y="true">
					<view class="title_item" v-for="(item,index) in colList" :key="index" @click="setId(index)">
						{{item.title}}
					</view>
				</scroll-view>
			</view>
			
			<view class="right">
				<scroll-view scroll-y="true" style="white-space: nowrap;height: 170upx;" :scroll-into-view="clickId">
					<view v-for="(item,index) in colList" :key="index">
						<view class="title" :id="'po' + index">{{item.title}}</view>
						<view v-for="(v,k) in item.list" :key='k'>
							{{v}}
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
				colList:[{
					title:'热门推荐',
					list:['热门推荐一','热门推荐二','热门推荐三']
				},{
					title:'手机数码',
					list:['手机数码一','手机数码二','手机数码三']
				},{
					title:'电脑办公',
					list:['电脑办公一','电脑办公二','电脑办公三']
				},{
					title:'家用电器',
					list:['家用电器一','家用电器二','家用电器三']
				},{
					title:'美妆护肤',
					list:['美妆护肤一','美妆护肤二','美妆护肤三']
				},{
					title:'京东超市',
					list:['京东超市一','京东超市二','京东超市三']
				},{
					title:'个护清洁',
					list:['个护清洁一','个护清洁二','个护清洁三']
				}],
				
				// 联动点击的id
				clickId:''
			}
		},
		
		methods:{
			setId(index){
				console.log(index)
				this.clickId = "po" + index
			}
		}
	}
</script>

<style lang="scss" scoped>
	page{
		background-color: #f2f2f2;
	}
	
	.container{
		.col_box{
			display: flex;
			
			.left{
				width: 158upx;
				height: 58upx;
				
				.title_item{
					width: 156;
					height: 56;
					border: 1upx solid red;
					color: #333;
					font-size: 32upx;
					text-align: center;
					line-height: 58upx;
					
					&:hover{
						color: #fff;
						background-color: red;
					}
				}
			}
		
			.right{
				margin-left: 20upx;
				
			}
		}
	}
</style>