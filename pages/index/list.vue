<template>
	<view class="container">
		<view class="left">
			<view :class="flag == item.id?'select':'normal'" :id='item.id' @click="switchNav" v-for="(item,index) in list_category" :key='index'>
				{{item.name}}
			</view>
		</view>
		<view class="right">
			<view class="example-body">
				<view class="example-box">
					<uni-card isShadow='true' v-for="(i,index) in list" :key="index">
						<view class="" style="text-align: center;font-size: 14px;font-weight: bold;">
							{{i.className.name}}
						</view>
						<view class="" style="display: grid;grid-template-columns: repeat(3,33.3%);grid-row-gap: 20px;">
							<view class="" v-for="(j,index) in i.classGroup" :key="index" style="text-align: center;" @click="goDetail($event,index)">
								<image :src="'../../static/'+j.class_photo" mode="" style="width: 100%;height: 60px;"></image>
								<view class="">
									{{j.name}}
								</view>
							</view>
						</view>
					</uni-card>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				flag: '',
				list_category:'',
				list:'',
			}
		},
		methods: {
			switchNav: function(e) {
				this.flag = e.target.id
				this.list = require('../../static/data/category_list_' + this.flag)
			},
			goDetail(e,index){
				wx.setStorage({
					key:"id",
					data:this.list[0].classGroup[index].id
				})
				wx.redirectTo({
				  url: './new'
				})
			}
		},
		mounted() {
			this.list_category = require('../../static/data/category_list')
			this.flag = this.list_category[0].id
			this.list = require('../../static/data/category_list_478')
		}
	}
</script>

<style>
	.left {
		position: fixed;
		top: 0;
		width: 30%;
		height: 400px;
	}
	.right{
		width: 68%;
		float: right;
	}
	.select {
		padding: 20px 10px;
		text-align: center;
		background-color: #ffffff;
		border-left: 2px solid #EE0925;
		font-weight: bold;
		color: #EE0925;
	}

	.normal {
		padding: 20px 10px;
		text-align: center;
		background-color: #F4F4F4;
		border-bottom: 1px solid #f2f2f2;
	}
</style>
