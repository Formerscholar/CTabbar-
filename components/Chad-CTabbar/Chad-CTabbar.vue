<template>
	<div id="c-tabbar">
		<div v-for="(item,idx) in tabbarList" :key="idx" :class="idx === currentItem ? 'list current' :'list'"
			@click="changeCurrent(item,idx)">
			<div class="item">
				<image class="iconfont" :src="currentItem === idx ? item.ImgUrl: item.AcImgUrl" mode="img"></image>
				<p :style="{'color':currentItem === idx ?MainColor:ViceColor}">{{item.text}}</p>
			</div>
		</div>
		<div class="indicator" :style="{ 'backgroundColor': MainColor }"></div>
	</div>
</template>

<script>
	export default {
		props: {
			tabbarList: {
				type: Array,
				required: false,
				default: [{
						ImgUrl: '/static/c-tabbar/img/home.png',
						AcImgUrl: "/static/c-tabbar/img/home-c.png",
						text: '首页',
						router: '/agency',
					},
					{
						ImgUrl: '/static/c-tabbar/img/cart.png',
						AcImgUrl: "/static/c-tabbar/img/cart-c.png",
						text: '购物车',
						router: '/census',
					},
					{
						ImgUrl: '/static/c-tabbar/img/hot.png',
						AcImgUrl: "/static/c-tabbar/img/hot-c.png",
						text: '热门',
						router: '/workbench',
					},
					{
						ImgUrl: '/static/c-tabbar/img/file.png',
						AcImgUrl: "/static/c-tabbar/img/file-c.png",
						text: '文件',
						router: '/addressbook',
					},
					{
						ImgUrl: '/static/c-tabbar/img/my.png',
						AcImgUrl: "/static/c-tabbar/img/my-c.png",
						text: '我的',
						router: '/my',
					},
				]
			},
			//主色调 ：未选中图片颜色
			MainColor: {
				type: String,
				required: false,
				default: "#288afc"
			},
			//副色调 : 选中图片颜色 （建议白灰）
			ViceColor: {
				type: String,
				required: false,
				default: "#7f8c8d"
			}
		},
		data() {
			return {
				currentItem: 0,
				MainColor: this.MainColor,
				ViceColor: this.ViceColor,
			}
		},
		methods: {
			changeCurrent(item, idx) {
				this.currentItem = idx
				this.$router.push(item.router)
				//选中点击事件
				this.$emit("currentClick")
			},
		},
		watch: {
			$route: {
				handler(to, from) {
					if (to.meta.index == 0) {
						let that = this
						that.tabbarList.map((item, idx) => {
							if (item.router == to.path) {
								that.currentItem = idx
							}
						})
					}
				},
				immediate: true,
				deep: true,
			},
		},
	}
</script>

<style scoped lang="scss">
	#c-tabbar {
		position: fixed;
		bottom: 0;
		left: 0;
		right: 0;
		background-color: #fff;
		width: 100%;
		height: 70px;
		display: flex;
		justify-content: center;
		align-items: center;
		padding: 0 10px;
		box-sizing: border-box;


		.list {
			display: flex;
			position: relative;
			height: 70px;
			width: 70px;



			.item {
				position: relative;
				display: flex;
				justify-content: center;
				align-items: center;
				flex-direction: column;
				width: 100%;
				text-align: center;

				.iconfont {
					position: relative;
					display: block;
					width: 1.625rem;
					height: 1.625rem;
					text-align: center;
					transition: 0.5s;
				}

				p {
					font-weight: bold;
					font-size: 0.875rem;
					letter-spacing: 1px;
					opacity: 0.8;
				}
			}
		}

		.current {
			.item {
				.iconfont {
					transform: translateY(-24px);
					z-index: 1;
				}

				p {
					opacity: 1;
				}
			}
		}

		.indicator {
			position: absolute;
			top: -50%;
			width: 60px;
			height: 60px;
			border-radius: 50%;
			border: 0.375rem solid #f8f8f8;
			transition: 0.5s;

			&::before {
				content: '';
				position: absolute;
				top: 50%;
				left: -1.375rem;
				width: 1.25rem;
				height: 1.25rem;
				background-color: transparent;
				border-top-right-radius: 1.25rem;
				box-shadow: 1px -0.625rem 0 0 #f8f8f8;
			}

			&::after {
				content: '';
				position: absolute;
				top: 50%;
				right: -1.375rem;
				width: 1.25rem;
				height: 1.25rem;
				background-color: transparent;
				border-top-left-radius: 1.25rem;
				box-shadow: -1px -0.625rem 0 0 #f8f8f8;
			}
		}

		.list:nth-child(1).current~.indicator {
			transform: translateX(calc(70px * -2));
		}

		.list:nth-child(2).current~.indicator {
			transform: translateX(calc(70px * -1));
		}

		.list:nth-child(3).current~.indicator {
			transform: translateX(calc(70px * 0));
		}

		.list:nth-child(4).current~.indicator {
			transform: translateX(calc(70px * 1));
		}

		.list:nth-child(5).current~.indicator {
			transform: translateX(calc(70px * 2));
		}
	}
</style>
