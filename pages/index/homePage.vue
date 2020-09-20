<template>
	<view class="container">
		<swiper class="swiper" indicator-dots="true" autoplay="true" interval="3000" duration="1000">
			<block v-for="(item,index) in pictrue" :key="index">
				<swiper-item>
					<image :src="item.url" class="slide-image" mode="aspectFill" style="width: 100%;height: 100%;" />
				</swiper-item>
			</block>
		</swiper>
		<view>
			<view class="uni-flex uni-row" style="margin-top: 30px;">
				<view class="flex-item">
					<image src="../../static/images/week.png" style="width: 30px;height: 30px;"></image>
					<text style="display: block;">每周上新</text>
				</view>
				<view class="flex-item">
					<image src="../../static/images/new.png" style="width: 30px;height: 30px;"></image>
					<text style="display: block;">新客专享</text>
				</view>
				<view class="flex-item">
					<image src="../../static/images/play.png" style="width: 30px;height: 30px;"></image>
					<text style="display: block;">天天直播</text>
				</view>
				<view class="flex-item">
					<image src="../../static/images/shake.png" style="width: 30px;height: 30px;"></image>
					<text style="display: block;">摇一摇</text>
				</view>
				<view class="flex-item">
					<image src="../../static/images/limit.png" style="width: 30px;height: 30px;"></image>
					<text style="display: block;">限时特惠</text>
				</view>
			</view>
		</view>
		<view>
			<view class="uni-flex uni-row" style="margin-top: 30px;">
				<view class="flex-item">
					<image src="../../static/images/low.png" style="width: 30px;height: 30px;"></image>
					<text style="display: block;">低温速食</text>
				</view>
				<view class="flex-item">
					<image src="../../static/images/meat.png" style="width: 30px;height: 30px;"></image>
					<text style="display: block;">品质肉禽</text>
				</view>
				<view class="flex-item">
					<image src="../../static/images/fruit.png" style="width: 30px;height: 30px;"></image>
					<text style="display: block;">新鲜水果</text>
				</view>
				<view class="flex-item">
					<image src="../../static/images/gh.png" style="width: 30px;height: 30px;"></image>
					<text style="display: block;">粮油干货</text>
				</view>
				<view class="flex-item">
					<image src="../../static/images/water.png" style="width: 30px;height: 30px;"></image>
					<text style="display: block;">生活水饮</text>
				</view>
			</view>
		</view>
		<view v-for="(item,index) in list.bannerTags" :key='index' style="margin-top: 10px;margin-bottom: 10px;">
			<view style="display: flex;justify-content: center;">
				<image :src="'../../static/'+item.image" style="height: 60px;"></image>
			</view>
			<view>
				<scroll-view class="scroll-view_H" scroll-x="true" @scroll="scroll" scroll-left="120">
					<view id="demo1" class="scroll-view-item_H">
						<view class="uni-flex uni-row" style="display: flex;justify-content: space-evenly;">
							<view class="flex-item" v-for="(i,index) in item.content" :key='index' v-if="index<3" @click="goDetail" :id='i.product_id'>
								<image :src="'../../static/'+i.image" style="width: 70px;height: 70px;"></image>
								<view class="font">{{i.subtitle}}</view>
								<view class="font">{{i.title}}</view>
								<view style="display: flex;align-items: center;justify-content: center;">{{i.price}}/kg<image src="../../static/images/cart.png" style="width: 15px;height: 15px;"></image></view>
							</view>
						</view>
					</view>
					<view id="demo2" class="scroll-view-item_H">
						<view class="uni-flex uni-row" style="display: flex;justify-content: space-evenly;">
							<view class="flex-item" v-for="(i,index) in item.content" :key='index' v-if="index>=3&&index<6">
								<image :src="'../../static/'+i.image" style="width: 70px;height: 70px;"></image>
								<view class="font">{{i.subtitle}}</view>
								<view class="font">{{i.title}}</view>
								<view style="display: flex;align-items: center;justify-content: center;">{{i.price}}/kg<image src="../../static/images/cart.png" style="width: 15px;height: 15px;"></image></view>
							</view>
						</view>
					</view>
					<view id="demo3" class="scroll-view-item_H">
						<view class="uni-flex uni-row" style="display: flex;justify-content: space-evenly;">
							<view class="flex-item" v-for="(i,index) in item.content" :key='index' v-if="index>=6&&index<9">
								<image :src="'../../static/'+i.image" style="width: 70px;height: 70px;"></image>
								<view class="font">{{i.subtitle}}</view>
								<view class="font">{{i.title}}</view>
								<view style="display: flex;align-items: center;justify-content: center;">{{i.price}}/kg<image src="../../static/images/cart.png" style="width: 15px;height: 15px;"></image></view>
							</view>
						</view>
					</view>
					<view id="demo4" class="scroll-view-item_H" v-show="false">
						<view class="uni-flex uni-row" style="display: flex;justify-content: space-evenly;">
							<view class="flex-item" v-for="(i,index) in item.content" :key='index' v-if="index>9">
								<image :src="'../../static/'+i.image" style="width: 70px;height: 70px;"></image>
								<view class="font">{{i.subtitle}}</view>
								<view class="font">{{i.title}}</view>
								<view style="display: flex;align-items: center;justify-content: center;">{{i.price}}/kg<image src="../../static/images/cart.png" style="width: 15px;height: 15px;"></image></view>
							</view>
						</view>
					</view>
				</scroll-view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				scrollTop: 0,
				old: {
					scrollTop: 0
				},
				pictrue: [{
						url: "../../static/images/banner-1.jpg"
					},
					{
						url: "../../static/images/banner-2.jpg"
					},
					{
						url: "../../static/images/banner-3.jpg"
					},
					{
						url: "../../static/images/banner-4.jpg"
					},
					{
						url: "../../static/images/banner-5.jpg"
					},
				],
				list: '',
				list2:''
			}
		},
		methods: {
			scroll: function(e) {
				this.old.scrollTop = e.detail.scrollTop
			},
			goDetail(e){
				wx.setStorage({
					key:"list_id",
					data:e.currentTarget.id
				})
				wx.redirectTo({
				  url: './detail'
				})
			}
		},
		mounted() {
			let a = require('../../static/data/fruits.json')
			this.list = a
			console.log(this.list)
		},
	}
</script>

<style>
	.font{
		white-space: nowrap;
		overflow: hidden;
		text-overflow: ellipsis;
	}
	.flex-item {
		width: 30%;
		text-align: center;
		font-size: 12px;
	}

	.text {
		margin: 15rpx 10rpx;
		padding: 0 20rpx;
		background-color: #ebebeb;
		height: 70rpx;
		line-height: 70rpx;
		text-align: center;
		color: #777;
		font-size: 26rpx;
	}

	.scroll-view_H {
		white-space: nowrap;
		width: 100%;
	}
	.scroll-view-item_H {
		display: inline-block;
		width: 100%;
		height: 300rpx;
		line-height: 300rpx;
		text-align: center;
	}
</style>
