<template>
	<view class="view-my">
		<!-- <view type="flex" align="center" class="poster margin-bottom-10">
			<view span="8" class="poster-headimg"><image :src="member.headImgUrl" class="head-image" /></view>
			<view span="16">
				<view class="poster-name margin-bottom-10">{{ member.name }}</view>
				<view class="poster-name" v-if="member.customerName">{{ member.customerName }}</view>
			</view>
		</view> -->

		<view class="my-header">
			<view class="view-header-img">
				<view class="header-img-view"><img class="header-img" src="@/static/images/pages/my/my_icon_head.png" /></view>
			</view>
			<view class="view-header-member">
				<view class="header-member-view">
					<view class="view-member-link">注册/登录</view>
					<view class="view-member-explain">登录后享受更多优惠及服务</view>
				</view>
			</view>
		</view>
		<view class="my-body">
			<view class="my-body-view">
				<view class="my-body-row">
					<view class="my-body-col body-col-course">
						<view class="col-icon-view col-icon-course">
							<view class="icon-img-view"><img class="col-icon-img" src="@/static/images/pages/my/my_icon_course.png" /></view>
						</view>
						<view class="body-col-title">我的课程</view>
					</view>
					<view class="my-body-col body-col-card">
						<view class="col-icon-view col-icon-card">
							<view class="icon-img-view"><img class="col-icon-img" src="@/static/images/pages/my/my_icon_card.png" /></view>
						</view>
						<view class="body-col-title">会员卡</view>
					</view>
				</view>
				<view class="my-body-row">
					<view class="my-body-col body-col-search">
						<view class="col-icon-view col-icon-search">
							<view class="icon-img-view"><img class="col-icon-img" src="@/static/images/pages/my/my_icon_search.png" /></view>
						</view>
						<view class="body-col-title">上课记录查询</view>
					</view>
					<view class="my-body-col body-col-evaluate">
						<view class="col-icon-view col-icon-evaluate">
							<view class="icon-img-view"><img class="col-icon-img" src="@/static/images/pages/my/my_icon_evaluate.png" /></view>
						</view>
						<view class="body-col-title">我的评价</view>
					</view>
				</view>
				<view class="my-body-row">
					<view class="my-body-col body-col-integral">
						<view class="col-icon-view col-icon-integral">
							<view class="icon-img-view"><img class="col-icon-img" src="@/static/images/pages/my/my_icon_integral.png" /></view>
						</view>
						<view class="body-col-title">我的积分</view>
					</view>
					<view class="my-body-col body-col-data">
						<view class="col-icon-view col-icon-data">
							<view class="icon-img-view"><img class="col-icon-img" src="@/static/images/pages/my/my_icon_data.png" /></view>
						</view>
						<view class="body-col-title">完善资料</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
import defaultHeadImg from '@/static/images/pages/portrait_bg.png';
import memberService from '@/services/memberService.js';

export default {
	data() {
		return {};
	},
	computed: {
		headImgUrl() {
			return this.member.headImgUrl || defaultHeadImg;
		},
		member() {
			return memberService.getMember();
		}
	},
	methods: {
		onMyTicket() {
			uni.navigateTo({
				url: '/pages/member/my-ticket'
			});
		},
		onMyFace() {
			uni.navigateTo({
				url: '/pages/member/enroll-face'
			});
		}
	}
};
</script>

<style lang="scss" scoped>
.view-my {
	background: #ebebeb;
	min-height: calc(100vh - 50px);
	.my-header {
		background: url('@/static/images/pages/my/my_header_background.png');
		background-size: 100% 100%;
		height: 190px;
		.view-header-img {
			position: absolute;
			z-index: 2;
			top: 50px;
			width: 100%;
			.header-img-view {
				width: 60px;
				height: 60px;
				margin: 0 auto;
				.header-img {
					width: 100%;
					height: 100%;
				}
			}
		}

		.view-header-member {
			text-align: center;
			padding: 80px 15px 0px 15px;
			.header-member-view {
				background: #ffffff;
				padding: 45px 0px 25px 0px;
				border-radius: 15px;
				margin: 0 auto;
				.view-member-link {
					font-size: 20px;
				}
				.view-member-explain {
					font-size: 15px;
					color: #b2b2b2;
					padding: 7px 0px 0px 0px;
				}
			}
		}
	}
	.my-body {
		padding: 32px 15px 20px 15px;
		.my-body-view {
			background: #ffffff;
			border-radius: 15px;
			overflow: hidden;
			.my-body-row {
				display: flex;
				justify-content: space-between;
				align-items: center;
				.my-body-col {
					text-align: center;
					color: #4c4c4c;
					padding: 20px 0px 20px 0px;
					width: 50%;
					
						border-right: 1px solid #e6e6e6;
						border-bottom: 1px solid #e6e6e6;
					.col-icon-view {
						margin: 0 auto;
						width: 70px;
						height: 70px;
						border-radius: 50%;
						display: flex;
						align-items: center;
						.icon-img-view {
							margin: 0 auto;
							display: flex;
							align-items: center;
							.col-icon-img {
								width: 30px;
								height: 30px;
							}
						}
					}
					.body-col-title{
						margin-top: 10px;
					}
				}
				.body-col-course {
					.col-icon-course {
						background: -webkit-linear-gradient(left, #35b1ff, #024cff);
						background: linear-gradient(to bottom, #35b1ff, #024cff);
					}
				}
				.body-col-card {
					.col-icon-card {
						background: -webkit-linear-gradient(left, #ffa101, #ed7126);
						background: linear-gradient(to bottom, #ffa101, #ed7126);
					}
				}
				.body-col-search {
					.col-icon-search {
						background: -webkit-linear-gradient(left, #951eda, #5d2afe);
						background: linear-gradient(to bottom, #951eda, #5d2afe);
					}
				}
				.body-col-evaluate {
					.col-icon-evaluate {
						background: -webkit-linear-gradient(left, #07d259, #00913a);
						background: linear-gradient(to bottom, #07d259, #00913a);
					}
				}
				.body-col-integral {
					border-bottom: 0px;
					.col-icon-integral {
						background: -webkit-linear-gradient(left, #ffa200, #ed7126);
						background: linear-gradient(to bottom, #ffa200, #ed7126);
					}
				}
				.body-col-data {
					border-bottom: 0px;
					.col-icon-data {
						background: -webkit-linear-gradient(left, #35b1ff, #014aff);
						background: linear-gradient(to bottom, #35b1ff, #014aff);
					}
				}
			}
		}
	}
}
</style>
