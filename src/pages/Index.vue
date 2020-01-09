<template>
	<q-page class="app-gateway" :style="`--background: url('${bg_image}')`">
		<!-- <q-page class="app-gateway"> -->
		<div class="app-gateway__content">
		<FrequentlyUsedApps></FrequentlyUsedApps>
		<TopFiveApps v-if="categories_tab == 'travel'"></TopFiveApps>
		<ShpTopFiveApps v-if="categories_tab == 'shop'"></ShpTopFiveApps>	
		<GamesTopFiveApps v-if="categories_tab == 'games'"></GamesTopFiveApps>		
		<MusicTopFiveApps v-if="categories_tab == 'music'"></MusicTopFiveApps>		
		<FoodTopFiveApps v-if="categories_tab == 'food'"></FoodTopFiveApps>	
		<TravelDestinations v-if="categories_tab == 'travel'"></TravelDestinations>
		<Shop v-if="categories_tab == 'shop'"></Shop>
		<Games v-if="categories_tab == 'games'"></Games>
		<Music v-if="categories_tab == 'music'"></Music>
		<Food v-if="categories_tab == 'food'"></Food>
		</div>
		<q-page-sticky expand position="top" style="z-index: 10">
		<div
			v-scroll="scrolled"
			class="swiper-container categories-tab"
			:style="
			filled_header >= 20
				? 'background-color: #202124 !important'
				: 'background-color: transparent'
			"
		>
			<div class="swiper-wrapper">
			<div
				class="swiper-slide"
				:class="categories_tab == cat.name ? 'tab-active' : ''"
				v-for="(cat, i) in categories"
				:key="i"
				@click="categories_tab = cat.name"
			>
				<div class="categories-tab__item">
				<div class="categories-tab__item-icon">
					<img width="22" :src="cat.icon" alt />
				</div>
				<div class="categories-tab__item-name">{{ cat.name }}</div>
				</div>
			</div>
			</div>
		</div>
		</q-page-sticky>
	</q-page>
</template>

<script>
import Swiper from "swiper";
import "swiper/css/swiper.min.css";

import FrequentlyUsedApps from "../components/FrequentlyUsedApps";
import TopFiveApps from "../components/TopFiveApps";
import TravelDestinations from "../components/TravelDestinations";
const Shop 				= () => import(/*webpackChunkname: 'shop'*/ "../components/Shop");
const ShpTopFiveApps 	= () => import(/*webpackChunkname: 'shop-top-five'*/ "../components/ShpTopFiveApps");
const Games 			= () => import(/*webpackChunkname: 'games'*/ "../components/Games");
const GamesTopFiveApps 	= () => import(/*webpackChunkname: 'games-top-five'*/ "../components/GamesTopFiveApps");
const Music 			= () => import(/*webpackChunkname: 'music'*/ "../components/Music");
const MusicTopFiveApps 	= () => import(/*webpackChunkname: 'music-top-five'*/ "../components/MusicTopFiveApps");
const Food 				= () => import(/*webpackChunkname: 'food'*/ "../components/Food");
const FoodTopFiveApps 	= () => import(/*webpackChunkname: 'food-top-five'*/ "../components/FoodTopFiveApps");

export default {
	name: "PageIndex",
	components: {
		FrequentlyUsedApps,
		TopFiveApps,
		ShpTopFiveApps,
		GamesTopFiveApps,
		MusicTopFiveApps,
		FoodTopFiveApps,
		TravelDestinations,
		Shop,
		Games,
		Music,
		Food
	},
	data() {
		return {
		filled_header: 20,
		categories_tab: "travel",
		bg_image: "../statics/get-started.jpg",
		categories: [
			{
			icon: "statics/cat-travel.svg",
			name: "travel"
			},
			{
			icon: "statics/cat-shop.svg",
			name: "shop"
			},
			{
			icon: "statics/cat-games.svg",
			name: "games"
			},
			{
			icon: "statics/cat-music.svg",
			name: "music"
			},
			{
			icon: "statics/cat-food.svg",
			name: "food"
			}
		]
		};
	},
	methods: {
		scrolled(position) {
		this.filled_header = position;
		},
		openWebsite(website) {
		window.open(website, "_blank");
		},
		toggleCategories(name) {
		this.categories_tab = name;
		this.categories.name = this.categories_tab;
		}
	},
	mounted() {
		var mySwiper = new Swiper(".swiper-container", {
		slidesPerView: 5
		});
		this.scrolled();
		//this.toggleCategories();
	}
};
</script>

<style lang="scss">
.section-title {
	color: #fff;
	font-size: 12px;
	padding: 0 14px;
}

.app-gateway {
	position: relative;
	--background: #fff;
	overflow: hidden;
	// background-color: #202124;

	&::after {
		content: " ";
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		background-size: cover;
		background-position: center;
		background-image: var(--background);
		height: 100vh;
		z-index: 1;
		filter: blur(8px);
	}

	.swiper-container {
		width: 100%;
		padding-top: 1rem;
		border-bottom: 1px solid rgba(#fff, 0.1);
		// background-color: #202124;

		.swiper-wrapper {
		.swiper-slide {
			display: flex;
			align-items: center;
			justify-content: center;
			padding-bottom: 8px;
		}
		}

		.categories-tab__item {
		text-align: center;

		.categories-tab__item-icon {
			background-color: $storya;
			border-radius: 100%;
			width: 45px;
			height: 45px;
			display: flex;
			align-items: center;
			justify-content: center;

			img {
			max-width: 100%;
			height: auto;
			}
		}

		.categories-tab__item-name {
			text-transform: capitalize;
			color: #fff;
			font-size: 0.75rem;
			text-align: center;
			width: 45px;
			margin-top: 4px;
		}
		}
	}

	.tab-active {
		border-bottom: 1px solid $storya;

		.categories-tab__item-name {
		color: $storya !important;
		}
	}

	&__content {
		padding-top: 110px;
		position: relative;
		z-index: 3;
	}
}
</style>
