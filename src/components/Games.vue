<template>
  <div>
    <div class="gateway-category-tab">
      <div class="section-title">GAMES</div>
      <div class="swiper-wrapper">
        <div
          class="swiper-slide"
          :class="dest.active ? 'tab-active' : ''"
          v-for="(dest, i) in games"
          :key="i"
          @click="selectActive(i)"
        >
          <div class="sub-category">
            <div class="sub-category__icon">
              <img class="swiper-lazy" :data-src="dest.icon" alt="" />
              <q-spinner size="2em" color="white" class="swiper-preloader"></q-spinner>
            </div>
            <div class="sub-category__name">{{ dest.name }}</div>
          </div>
        </div>
      </div>
    </div>
    <div class="gateway-category-panel">
      <div
        class="gateway-category-panel__item"
        v-for="(dest, index) in filterGames"
        :key="index"
      >
        <div class="swiper-wrapper">
          <div
            class="swiper-slide"
            v-for="(item, ind) in dest.lists"
            :key="ind"
            @click="openWebsite(item.website)"
          >
            <img class="swiper-lazy" :data-src="item.image" alt="" />
            <div class="desc">{{ item.desc }}</div>
            <div class="website">{{ item.website }}</div>
            <q-spinner size="2em" color="white" class="swiper-preloader"></q-spinner>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Swiper from "swiper";
import "swiper/css/swiper.min.css";

export default {
  props: {
    name: String
  },
  data() {
    return {
      games: [
        {
          icon: "statics/games/games-all.jpg",
          name: "all",
          active: true,
          lists: [
            {
              image: "statics/games/07.jpg",
              desc: "The most watched esports events of November 2019",
              website: "https://esportsinsider.com/"
            },
            {
              image: "statics/games/04.jpg",
              desc: "Best Apps for Kids Age 5–8",
              website: "https://www.commonsensemedia.org/"
            }
          ]
        },
        {
          icon: "statics/games/games-adventure.jpg",
          name: "adventure",
          active: false,
          lists: [
            {
              image: "statics/games/01.jpg",
              desc: "The 25 Best Adventure Games",
              website: "https://www.popularmechanics.com/"
            },
            {
              image: "statics/games/02.jpg",
              desc: "20 terrifying PC horror games to play with the lights off",
              website: "https://www.pcworld.com/"
            }
          ]
        },
        {
          icon: "statics/games/games-educational.jpg",
          name: "educational",
          active: false,
          lists: [
            {
              image: "statics/games/03.jpg",
              desc: "10 Top Educational Apps For Kids",
              website: "https://elearningindustry.com/"
            },
            {
              image: "statics/games/04.jpg",
              desc: "Best Apps for Kids Age 5–8",
              website: "https://www.commonsensemedia.org/"
            }
          ]
        },
        {
          icon: "statics/games/games-extreme.jpg",
          name: "extreme",
          active: false,
          lists: [
            {
              image: "statics/games/05.jpg",
              desc: "12 Horrifyingly Violent Video Games",
              website: "https://www.rollingstone.com/"
            },
            {
              image: "statics/games/06.jpg",
              desc: "Top 100 Extreme Game sites",
              website: "http://www.xtremetop100.com/"
            }
          ]
        },
        {
          icon: "statics/games/games-fun.jpg",
          name: "fun",
          active: false,
          lists: [
            {
              image: "statics/games/07.jpg",
              desc: "The most watched esports events of November 2019",
              website: "https://esportsinsider.com/"
            },
            {
              image: "statics/games/08.jpg",
              desc: "Dota 2 update brings back strict solo matchmaking",
              website: "https://dotesports.com/"
            }
          ]
        }
      ]
    };
  },
  computed: {
    filterGames() {
      return this.games.filter(res => res.active);
    }
  },
  methods: {
    selectActive(ind) {
      this.games.forEach((dest, index) => (this.games[index].active = false));
      this.games[ind].active = true;
    },
    openWebsite(link) {
      window.open(link, "_blank");
    }
  },
  mounted() {
    var mySwiper = new Swiper(".gateway-category-tab", {
      slidesPerView: 5,
      spaceBetween: 15,
      slidesOffsetAfter: 30,
      preloadImages: false,
      lazy: {
        preloaderClass: "swiper-preloader"
      }
    });

    var mySwiper2 = new Swiper(".gateway-category-panel__item", {
      slidesPerView: 2,
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
