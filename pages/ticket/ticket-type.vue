<template>
	<view class="view-ticket-type">
		<swiper autoplay circular interval="5000" :duration="150" class="image-swiper">
			<swiper-item v-for="(item, index) in iceSwipers" :key="index">
				<view class="view-image">
					<view class="image-view"><img class="ice-image" :src="item" /></view>
					<view class="image-text">
						<view class="text-view">图片{{ index + 1 }}/{{ iceSwipers.length }}张</view>
					</view>
				</view>
			</swiper-item>
		</swiper>
		<view class="view-ticket">
			<view class="ticket-title">冰场滑冰俱乐部</view>
			<view class="ticket-explain">
				<view class="explain-tap">正常营业</view>
				<view class="explain-tap">最早8:00入场</view>
				<view class="explain-introduction">
					课程介绍
					<view class="introduction-icon"><img class="introduction-right-img" src="@/static/images/pages/ticket-type/ice_icon_right.png" /></view>
				</view>
			</view>
			<view class="ticket-map">
				<view class="iconfont icon-location"></view>
				<view class="location-text">深圳市宝安区新安街道扬田路德志高工业园</view>
				<view class="map-link">
					地图
					<text class="iconfont icon-arrow"></text>
				</view>
			</view>
			<view class="view-ticket-type">
				<view v-for="ticketType in ticketTypes" :key="ticketType.id" class="ticket-type-view">
					<view class="ticket-type-left">
						<view class="ticket-type-title">{{ ticketType.name }}</view>
						<view class="ticket-status-view">
							<text :style="{ color: getRefundColor(ticketType) }">{{ ' ' + ticketType.refundText + ' ' }}</text>
							<view class="status-separate"></view>
							<text class="status-take">无需取票</text>
							<view class="status-separate"></view>
							<text class="trave-date-text">{{ ticketType.travelDateText }}</text>
						</view>
						<view class="ticket-introduction">
							<view class="introduction-tap">新品</view>
							<view class="introduction-link">购票须知 ></view>
						</view>
					</view>
					<view class="ticket-type-right">
						<view class="ticket-price-view">
							<text class="ticket-price-symbol">￥</text>
							<text class="ticket-price-value">{{ ticketType.price }}</text>
						</view>
						<view class="view-ticket-button">
							<view class="ticket-button-view" @click="onBuy(ticketType)"><button class="book-button">立即预订</button></view>
						</view>
					</view>
				</view>
			</view>
		</view>
		<tui-toast ref="toast"></tui-toast>
	</view>
</template>

<script>
import iIceSwiperOne from '@/static/images/pages/ticket-type/ice_swiper_one.jpg';
import iIceSwiperTwo from '@/static/images/pages/ticket-type/ice_swiper_two.jpg';
import iIceSwiperThree from '@/static/images/pages/ticket-type/ice_swiper_three.jpg';
import iIceSwiperFour from '@/static/images/pages/ticket-type/ice_swiper_four.jpg';
import iIceSwiperFive from '@/static/images/pages/ticket-type/ice_swiper_five.jpg';

export default {
	data() {
		return {
			iceSwipers: [iIceSwiperOne, iIceSwiperTwo, iIceSwiperThree, iIceSwiperFour, iIceSwiperFive],
			ticketTypes: [
				{
					name: '单次滑冰票（90分钟）',
					id: 1,
					travelDateText: '可订明日票',
					refundText: '有条件退',
					allowRefund: false,
					refundLimited: 1,
					price: 210
				},
				{
					name: '单次滑冰票（90分钟）',
					id: 2,
					travelDateText: '可订明日票',
					refundText: '有条件退',
					allowRefund: false,
					refundLimited: 1,
					price: 210
				},
				{
					name: '单次滑冰票（90分钟）',
					id: 3,
					travelDateText: '可订明日票',
					refundText: '有条件退',
					allowRefund: false,
					refundLimited: 1,
					price: 210
				},
				{
					name: '单次滑冰票（90分钟）',
					id: 4,
					travelDateText: '可订明日票',
					refundText: '有条件退',
					allowRefund: false,
					refundLimited: 1,
					price: 210
				},
				{
					name: '单次滑冰票（90分钟）',
					id: 5,
					travelDateText: '可订明日票',
					refundText: '有条件退',
					allowRefund: false,
					refundLimited: 1,
					price: 210
				}
			]
		};
	},
	onLoad() {
		this.getLocation();
	},
	methods: {
		getLocation() {
			let self = this;
			uni.getLocation({
				type: 'wgs84',
				success: function(res) {
					console.log('当前位置的经度：' + res.longitude);
					console.log('当前位置的纬度：' + res.latitude);
				},
				fail: function(res) {
					console.log(res);
					self.$refs.toast.show({
						title: '操作失败',
						imgUrl: '/static/images/toast/check-circle.png',
						icon: false
					});
				}
			});
		},
		getRefundColor(ticketType) {
			if (ticketType.allowRefund === false) {
				return '#ff2f39';
			}
			return ticketType.refundLimited ? '#fe7e18' : '#099fde';
		}
	}
};
</script>

<style lang="scss">
.view-ticket-type {
	.image-swiper {
		height: 200px;
		.view-image {
			.image-view {
				height: 100%;
				width: 100%;
				.ice-image {
					width: 100%;
					height: 100%;
				}
			}
			.image-text {
				width: 100%;
				position: absolute;
				top: 150px;
				.text-view {
					text-align: center;
					padding: 0px 4px 1px 11px;
					background: #adadad;
					color: #ffffff;
					border-radius: 25px;
					margin: 0 auto;
					opacity: 0.9;
				}
			}
		}
	}

	.view-ticket {
		border-top-left-radius: 15px;
		border-top-right-radius: 15px;
		overflow: hidden;
		margin-top: -15px;
		position: absolute;
		background: #ffffff;
		width: 100%;
		padding: 20px 0px 15px 0px;
		.ticket-title {
			font-size: 23px;
			padding: 0px 15px 0px 15px;
		}
		.ticket-explain {
			padding: 2px 15px 10px 15px;
			display: flex;
			align-items: center;
			font-size: 12px;
			color: #008ee5;
			.explain-tap {
				background: #d1eeff;
				padding: 1px 8px 1px 8px;
				margin-right: 5px;
				border-radius: 5px;
			}
			.explain-introduction {
				display: flex;
				padding: 0px 0px 0px 6px;
				.introduction-icon {
					padding: 0px 0px 0px 2px;
					.introduction-right-img {
						width: 9px;
						height: 10px;
					}
				}
			}
		}
		.ticket-map {
			border-top: 1px solid #dbdbdb;
			display: flex;
			justify-content: space-between;
			align-items: center;
			font-size: 12px;
			padding: 15px 15px 0px 15px;
			color: #666666;
			.iconfont {
				color: #666666;
			}
			.icon-location {
				font-size: 14px;
			}
			.icon-arrow {
				font-size: 12px;
			}
			.location-text {
				padding: 0px 2px 0px 2px;
				width: calc(100% - 60px);
			}
			.map-link {
			}
		}
		.view-ticket-type {
			padding: 15px 0px 0px 0px;
			.ticket-type-view {
				border-top: 1px solid #dbdbdb;
				padding: 15px 15px 10px 15px;
				display: flex;
				justify-content: space-between;
				align-items: center;
				.ticket-type-left {
					.ticket-type-title {
						font-size: 17px;
					}
					.ticket-status-view {
						display: flex;
						align-items: center;
						font-size: 12px;
						padding: 7px 0px 7px 0px;
						.trave-date-text {
							color: #00b994;
						}
						.status-take {
							color: #666666;
						}
						.status-separate {
							border-right: 1px solid #666666;
							width: 0px;
							margin-left: 4px;
							margin-right: 4px;
							height: 12px;
						}
					}
					.ticket-introduction {
						display: flex;
						align-items: center;
						.introduction-tap {
							color: #ffffff;
							font-size: 12px;
							padding: 0px 7px 0px 7px;
							border-top-left-radius: 10px;
							border-bottom-right-radius: 10px;
							background: -webkit-linear-gradient(left, #1ea9ff, #0fc5e2);
							background: linear-gradient(to right, #1ea9ff, #0fc5e2);
						}
						.introduction-link {
							padding: 0px 0px 0px 8px;
							color: #666666;
							font-size: 13px;
						}
					}
				}
				.ticket-type-right {
					text-align: center;
					.ticket-price-view {
						color: #ff6200;
						padding: 0px 0px 5px 0px;
						.ticket-price-symbol {
							font-size: 12px;
						}
						.ticket-price-value {
							font-size: 20px;
						}
					}
					.book-button {
						border-radius: 25px;
						padding: 7px 13px 7px 13px;
						background: -webkit-linear-gradient(left, #fc5417, #fe7d18);
						background: linear-gradient(to right, #fc5417, #fe7d18);
					}
				}
			}
		}
	}
}
</style>

<style>
.text-view {
	width: 160rpx;
}
</style>
