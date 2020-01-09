<template>
	<div>
		<div class="top-five-apps">
		<div class="section-title">TOP 5 APPS</div>
		<div class="swiper-wrapper">
			<div class="swiper-slide" @click="showAppDetails(i, app)" v-for="(app, i) in apps" :key="i">
				<div class="app-icon">
					<img class="swiper-lazy" :data-src="app.icon"  />
				</div>
				<q-spinner size="2em" color="white" class="swiper-preloader"></q-spinner>
			</div>
		</div>
		</div>
		<q-dialog maximized transition-show="fade" transition-hide="fade" v-model="dialog">
		<q-card class="q-pb-lg" style="background-color: #202124">
			<button class="app-back" style="margin-left: 12px" @click="dialog = false">
			<q-icon size="20px" color="white" name="mdi-keyboard-backspace"></q-icon>
			<div class="app-back__label">Back</div>
			</button>
			<div class="app-details">
			<div class="app-info">
				<div class="app-info__label">You are opening</div>
				<img :src="details.icon" alt />
				<div class="app-name">{{ details.name }}</div>
			</div>
			<div class="add-space">
				<img :src="details.add" :alt="details.add" />
			</div>
			<button v-ripple class="btn-app-continue">
				<div>CONTINUE TO {{ details.name }}</div>
				<div class="points">and receive 10 Points</div>
			</button>
			</div>
		</q-card>
		</q-dialog>
	</div>
</template>

<script>
import Swiper from "swiper";
import "swiper/css/swiper.min.css";

export default {
	data() {
		return {
		dialog: false,
		details: {},
		apps: [
			{
				icon: "statics/shop/shop-1.svg",
				name: "ebay",
				add:
					"https://image.cnbcfm.com/api/v1/image/106008977-156267514025104113-4_tacos_pr_images_cr.jpg?v=1562675184"
			},
				{
				icon: "statics/shop/shop-2.svg",
				name: "amazon",
				add:
					"https://assets1.csnews.com/files/styles/content_sm/s3/2018-02/McDonalds%20Happy%20Meal.jpg?itok=1ng0cLST"
			},
			{
				icon: "statics/shop/shop-3.svg",
				name: "lazada",
				add:
					"https://www.qsrmagazine.com/sites/default/files/styles/story_page/public/news-image/kfc-adds-fried-wings-menus-nationwide.jpg?itok=Z5J5ZZ3q"
			},
			{
				icon: "statics/shop/shop-4.svg",
				name: "shopee",
				add: "https://media.graytvinc.com/images/810*450/KFC30.jpg"
			},
			{
				icon: "statics/shop/shop-5.svg",
				name: "zalora",
				add:
					"https://cdn.rttnews.com/articleimages/ustopstories/2019/november/popeyeschickensandwich-nov04-lt.jpg"
			}
		]
		};
	},
	methods: {
		showAppDetails(id, app) {
			this.dialog = true;
			this.details.icon = app.icon;
			this.details.name = app.name;
			this.details.add = app.add;
		}
	},
	mounted() {
		var mySwiper = new Swiper(".top-five-apps", {
			slidesPerView: 5,
			spaceBetween: 15,
			slidesOffsetAfter: 30,
			preloadImages: false,
			lazy: {
				preloaderClass: "swiper-preloader"
			}
		});
	}
};
</script>