<template>
	<view class="container">
		<view class="wyb-tabs">
			<wyb-tabs :tabs="tabs" @change="onChange" scroll="true" :current="tabIndex" />
		</view>
		<view class="uni-flex uni-row" style="width: 100%;background-color: #F5F5F5;justify-content: space-evenly;height: 30px;align-items: center;">
			<view class="flex-item" @click="aven">综合</view>
			<view class="flex-item" @click="sales">销量</view>
			<view class="flex-item" @click="price">价格</view>
		</view>
		<view v-for="(i,index) in list.productGroup" :key='index' style="border-bottom: 1px solid #CCCCCC;">
			<view style="padding: 5px;display: flex;align-items: center;">
				<view style="margin-right: 5px;">
					<image :src="'../../static/'+i.photo" style="width: 100px;height: 100px;"></image>
				</view>
				<view>
					<view style="font-size: 13px;">{{i.product_name}}</view>
					<view style="margin-bottom: 15px;">{{i.product_desc}}</view>
					<view>{{i.volume}}</view>
					<view style="display: flex;align-items: center;">
						<view style="font-size: 14px;padding: 5px;color: #FF7200;">¥{{i.price}}</view>
						<view style="padding: 1px;color: white;background-color:#FF7200 ;">明日达</view>
						<image src="../../static/images/cart.png" style="width: 30px;height: 30px;"></image>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import wybTabs from '@/components/wyb-tabs/wyb-tabs.vue'
	export default {
		data() {
			return {
				list: [],
				id: '',
				tabs: [],
				tabIndex: '',
				name: '',
				all: [],
				list2:[]
			}
		},
		components: {
			wybTabs
		},
		methods: {
			onChange(e) {
				let label = e.label
				let index = e.index
				for (let i = 0; i < this.all.length; i++) {
					if (label == this.all[i].name) {
						this.list = this.all[i]
						this.list2 = JSON.parse(JSON.stringify(this.list.productGroup))
					}
				}
			},
			sales(){
				this.list.productGroup.sort(function(a,b){
					return a.sales - b.sales
				})
				console.log(this.list2,'sales')
			},
			price(){
				this.list.productGroup.sort(function(a,b){
					return a.price - b.price
				})
				console.log(this.list2,'price')
			},
			aven(){
				this.list.productGroup = JSON.parse(JSON.stringify(this.list2))
				console.log(this.list2,'aven')
			}
		},
		mounted() {
			this.id = wx.getStorageSync('id')
			if (this.id == 480) {
				this.list = require('../../static/data/sub_category_list_480')[0]
				this.list2 = JSON.parse(JSON.stringify(this.list.productGroup))	
				console.log(this.list2[0] == this.list.productGroup[0])
				this.tabs = [{
					label: '每周上新',
					activeColor: '#519900',
					sBlockColor: '#519900'
				}]
			} else {
				this.all = require('../../static/data/sub_category_list_0')
				for (let i = 0; i < this.all.length; i++) {
					if (this.id == this.all[i].id) {
						this.list = this.all[i]
						this.list2 = JSON.parse(JSON.stringify(this.list.productGroup))
						this.name = this.list.name
					}
				}
				this.tabs = [{
					label: '奇异果',
					activeColor: '#519900',
					sBlockColor: '#519900'
				}, {
					label: '苹果',
					activeColor: '#519900',
					sBlockColor: '#519900'
				}, {
					label: '橙柑橘柚',
					activeColor: '#519900',
					sBlockColor: '#519900'
				}, {
					label: '樱桃',
					activeColor: '#519900',
					sBlockColor: '#519900'
				}, {
					label: '梨',
					activeColor: '#519900',
					sBlockColor: '#519900'
				}, {
					label: '牛油果',
					activeColor: '#519900',
					sBlockColor: '#519900'
				}, {
					label: '热带水果',
					activeColor: '#519900',
					sBlockColor: '#519900'
				}]
				for (let i = 0; i < this.tabs.length; i++) {
					if (this.tabs[i].label == this.name) {
						this.tabIndex = i
					}
				}
			}
		}
	}
</script>

<style>
</style>
