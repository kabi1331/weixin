<template>
	<view class="container">
		<view style="background-color: #F2F1ED;margin: 15px;border-radius: 15px;">
			<view style="display: flex;flex-direction: row;justify-content: space-between;padding-top: 70rpx;">
				<view class="left">
					<image src="../../static/images/4.png" style="border-radius: 50%;width: 80px;height: 80px;"></image>
					<view style="display: flex;flex-direction:column;margin-left: 15px;">
						<navigator url="/pages/index/index" hover-class="navigator-hover" open-type="navigate">
							<text style="font-size: 24px;font-weight: bolder;">{{username}}</text>
						</navigator>
						<text style="color: white;background-color: #FF8700;border-radius: 16px;margin: 10px 0;
							padding: 3px 6px;width: 80px;text-align: center;">签到送好礼</text>
					</view>
				</view>
				<view class="right">
					<view style="background-color: #C2C2C2;padding:10px; border-bottom-left-radius: 50px;border-top-left-radius: 50px;">
						<uni-icons type="scan" size="36"></uni-icons>
					</view>
				</view>
			</view>
			<view style="display: flex;flex-direction: row;margin: 15px 30px;">
				<view style="display: flex;flex-direction: column;font-size: 16px;align-items: center;width: 25%;">
					<text>积分</text>
					<text style="font-weight: bold;">-</text>
				</view>
				<view style="display: flex;flex-direction: column;font-size: 16px;align-items: center;width: 25%;margin-bottom: 20px;">
					<text>资产·充值</text>
					<text style="font-weight: bold;">-</text>
				</view>
				<view style="display: flex;flex-direction: column;font-size: 16px;align-items: center;width: 25%;">
					<text>优惠券</text>
					<text style="font-weight: bold;">-</text>
				</view>
				<view style="display: flex;flex-direction: column;font-size: 16px;align-items: center;width: 25%;">
					<text>礼品</text>
					<text style="font-weight: bold;">-</text>
				</view>
			</view>
		</view>
		<!-- 第二大块 -->
		<view style="background-color:#F2F1ED ;border-radius: 15px;margin: 15px">
			<view style="display: flex;flex-direction: row;align-items: center;justify-content:space-between;margin: 0px 30px;padding-top: 20px;">
				<text style="font-size: 20px;">我的订单</text>
				<text style="font-size: 14px;font-weight: bold;">全部订单 ></text>
			</view>
			<view style="display: flex;flex-direction: row;padding: 30px 0;align-items: center;padding-bottom: 20px;">
				<view style="display: flex;flex-direction: column;width: 20%;align-items: center;
		">
					<uni-icons type="refreshempty" size="36"></uni-icons>
					<text>待付款</text>
				</view>
				<view style="display: flex;flex-direction: column;width: 20%;align-items: center;
		">
					<uni-icons type="qq" size="36"></uni-icons>
					<text>待发货</text>
				</view>
				<view style="display: flex;flex-direction: column;width: 20%;align-items: center;
		">
					<uni-icons type="cart-filled" size="36"></uni-icons>
					<text>待收货</text>
				</view>
				<view style="display: flex;flex-direction: column;width: 20%;align-items: center;
		">
					<uni-icons type="chat-filled" size="36"></uni-icons>
					<text>待评价</text>
				</view>
				<view style="display: flex;flex-direction: column;width: 20%;align-items: center;
						
		">
					<uni-icons type="more" size="36"></uni-icons>
					<text>待换货</text>
				</view>
			</view>
		</view>
		<!-- 第三大块 -->
		<view style="background-color:#F2F1ED;border-radius: 15px;margin: 0 15px;padding-bottom: 30px;">
			<view style="display: flex;flex-direction: row;align-items: center;justify-content:space-between;margin: 0px 30px;padding-top: 20px;">
				<text style="font-size: 20px;">充值有礼</text>
				<text style="font-size: 14px;font-weight: bold;">充值中心 ></text>
			</view>
			<view style="background-color: #EEEEEE;width: 200px;
		height: 65px;
		margin-left: 30px;
		margin-top: 15px;
		padding: 20px;
		">
				<view style="font-weight: bold;">￥<text style="font-size: 30px;">2000</text></view>
				<view style="color: orange;font-size: 14px;">送价值89.90元赠品</view>
			</view>
		</view>
		<!-- 第四大块 -->
		<view style="background-color:#F2F1ED ;border-radius: 15px;margin: 15px;font-size: 15px;">
			<view style="display: flex;flex-direction: row;padding: 30px 0;align-items: center;padding-bottom: 20px;flex-wrap: wrap">
				<view style="display: flex;flex-direction: column;width: 20%;align-items: center;">
					<uni-icons type="star-filled" size="36"></uni-icons>
					<text>会员中心</text>
				</view>
				<view style="display: flex;flex-direction: column;width: 20%;align-items: center;">
					<uni-icons type="videocam-filled" size="36"></uni-icons>
					<text>直播间</text>
				</view>
				<view style="display: flex;flex-direction: column;width: 20%;align-items: center;">
					<uni-icons type="heart-filled" size="36"></uni-icons>
					<text>天天新鲜屋</text>
				</view>
				<view style="display: flex;flex-direction: column;width: 20%;align-items: center;">
					<uni-icons type="flag-filled" size="36"></uni-icons>
					<text>卡券中心</text>
				</view>
				<view style="display: flex;flex-direction: column;width: 20%;align-items: center;">
					<uni-icons type="contact-filled" size="36"></uni-icons>
					<text>企业购</text>
				</view>
				<view style="display: flex;flex-direction: column;width: 20%;align-items: center;margin-top: 15px;">
					<uni-icons type="headphones" size="36"></uni-icons>
					<text>在线客服</text>
				</view>
				<view style="display: flex;flex-direction: column;width: 20%;align-items: center;margin-top: 15px;">
					<uni-icons type="help" size="36"></uni-icons>
					<text>我的问答</text>
				</view>
			</view>
		</view>

	</view>
</template>

<script>
	export default {

		data() {
			return {
				username: "登录/注册"
			}
		},
		methods: {

		},
		onShow() {
			const value = wx.getStorageSync('storage_key');
			if (value) {
				this.username = value
			} else {
				this.username = "登录/注册"
			}

		},

	}
</script>

<style>
	.left {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		margin-left: 30px;

	}

	.right {
		width: 100px;
		height: 50%;
		text-align: center;
	}
</style>
