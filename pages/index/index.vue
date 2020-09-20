<template>
	<view class="container">
		<view class="intro" style="display: flex;justify-content: space-between;">
			<input type="text" value="" placeholder="手机号" class="inp" v-model="userName"/>
			<view style="display: block;padding: 2px;background-color: #4CD964;color: white;height: 22px;position: relative;top: 10px;">获取验证码</view>
		</view>
		<view class="intro">
			<input type="text" value="" placeholder="短信验证码" class="inp" />
		</view>
		<text style="font-size: 12px;color: #808080;">首次用手机号登陆将自动为您注册，并有好礼相送</text>
		<view class="btn-area" id="buttonContainer">
			<button type="primary" @click='goHomepage'>登陆</button>
		</view>
		<view style="display: flex;justify-content: space-between;font-size: 12px;color: #FFB395;">
			<text >账号密码登陆</text>
			<text>未收到验证码？</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userName:''
			}
		},
		methods: {
			goHomepage(){
				wx.switchTab({url:'./homePage'})
				wx.setStorage({
					key:"storage_key",
					data:this.userName
				})
			}
		}
	}
</script>

<style>
	.container {
		padding: 20px;
		font-size: 14px;
		line-height: 24px;
	}
	.intro{
		border-bottom: 1px solid #CCCCCC;
		margin-top: 30px;
	}
	.inp{
		height: 50px;
		font-size: 15px;
	}
	#buttonContainer{
		margin-top: 30px;
	}
</style>
