<template>
	<view class="container">
		<swiper class="swiper" indicator-dots="true" autoplay="true" interval="3000" duration="1000" style="height: 300px;">
			<block v-for="(item,index) in list.templatePhoto" :key="index">
				<swiper-item>
					<image :src="'../../static/'+item" class="slide-image" mode="aspectFill" style="width: 100%;height: 100%;" />
				</swiper-item>
			</block>
		</swiper>
		<view class="example-body">
			<view class="example-box">
				<uni-card isShadow='true'>
					<view>
						{{list.productInfo.product_name.replace(/[^\u4e00-\u9fa5]/ig,"")}}
					</view>
					<view class=""> {{list.productInfo.product_desc}}</view>
					<view class="">¥{{list.productInfo.price}}</view>
					<view class="" v-for="(item,index) in list.productItem" :key="index">
						<view>
							{{item.volume}}
						</view>
					</view>
					<view>
						{{list.sendTimeMsg}}
					</view>
					<view>
						{{list.refundRule}}
					</view>
				</uni-card>
			</view>
		</view>
		<view v-for="(item,index) in list.templateInfo.desc_imgs" :key="index" style="height: 500px;">
			<image :src="'../../static/'+item" style="height: 500px;"></image>
		</view>
		<uni-goods-nav :fill="true" :options="options" :buttonGroup="buttonGroup" @click="onClick" @buttonClick="buttonClick" />
	</view>
</template>

<script>
	import uniGoodsNav from '@/components/uni-goods-nav/uni-goods-nav.vue'
	export default {
		data() {
			return {
				list: [],
				options: [{
					icon: 'cart',
					info: 0
				}, {
					icon: 'shop',
					text: '首页',
				}, {
					icon: 'scan',
					text: '分享',
				}],
				buttonGroup: [{
						text: '水果红包',
						backgroundColor: '#ff0000',
						color: '#fff'
					},
					{
						text: '加入购物车',
						backgroundColor: '#ffa200',
						color: '#fff'
					}
				],
				arr:[]
			}
		},
		components: {
			uniGoodsNav
		},
		mounted() {
			this.list = require('../../static/data/good_detail_' + wx.getStorageSync('list_id'))
		},
		methods: {
			onClick(e) {
				if (e.index == 1) {
					wx.switchTab({
						url: './homePage'
					})
				} else if (e.index == 0) {
					wx.switchTab({
						url: './car'
					})
					if(wx.getStorageSync('food')){
						this.arr = wx.getStorageSync('food')
						console.log(3)
						for(let i = 0;i<this.arr.length;i++){
							console.log(2)
							if(this.arr[i].name ==this.list.productInfo.product_name.replace(/[^\u4e00-\u9fa5]/ig, "")){
								this.arr[i].quantity+= parseInt(this.options[0].info)
								console.log(1)
								return
							}
						}
						this.arr.push({
							'id': this.arr == null?1:this.arr.length+1,
							'name': this.list.productInfo.product_name.replace(/[^\u4e00-\u9fa5]/ig, ""),
							'imgsrc': '../../static/images/product_pic/1-370x370-2404-XAR8915W.jpg',
							'href': '点击了商品请跳转至商品详情页',
							'attributes': this.list.productInfo.product_desc,
							'quantity': parseInt(this.options[0].info),
							'price': parseInt(this.list.productInfo.price)
						})
					}else{
						this.arr.push({
							'id': this.arr == null?1:this.arr.length+1,
							'name': this.list.productInfo.product_name.replace(/[^\u4e00-\u9fa5]/ig, ""),
							'imgsrc': '../../static/images/product_pic/1-370x370-2404-XAR8915W.jpg',
							'href': '点击了商品请跳转至商品详情页',
							'attributes': this.list.productInfo.product_desc,
							'quantity': parseInt(this.options[0].info),
							'price': parseInt(this.list.productInfo.price)
						})
					}
					console.log(this.arr)
					wx.setStorageSync('food', this.arr);
				}
			},
			buttonClick(e) {
				if (e.index == 1) {
					this.options[0].info++
				}
			}
		},
	}
</script>

<style>
</style>
