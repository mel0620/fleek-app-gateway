<template>
  <div>
    <div class="games">
      <div class="section-title">GAMES</div>
      <div class="swiper-wrapper">
        <div
          class="swiper-slide"
          :class="dest.active ? 'tab-active' : ''"
          v-for="(dest, i) in games"
          :key="i"
          @click="selectActive(i)"
        >
          <div class="games__item">
            <div class="games__item-icon">
              <img :src="dest.icon" alt="" />
            </div>
            <div class="games__item-name">{{ dest.name }}</div>
          </div>
        </div>
      </div>
    </div>
    <div class="games-panel">
      <div class="games-wrapper">
        <div
          class="games-item"
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
              <img :src="item.image" alt="" />
              <div class="desc">{{ item.desc }}</div>
              <div class="website">{{ item.website }}</div>
            </div>
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
              image: "statics/games/toy1.jpg",
              desc: "How to Help Your Child Make Friends",
              website: "https://www.parents.com/"
            },
            {
              image: "statics/games/appliances2.jpg",
              desc: "The 5 Best Affordable Luxury Appliance Brands",
              website: "https://blog.yaleappliance.com/"
            }
          ]
        },
        {
          icon: "statics/games/games-adventure.jpg",
          name: "adventure",
          active: false,
          lists: [
            {
              image: "statics/games/toy1.jpg",
              desc: "The 25 Best Adventure Games",
              website: "https://www.popularmechanics.com/"
            },
            {
              image: "statics/games/toy2.jpg",
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
              image: "statics/games/appliances1.jpg",
              desc: "10 Top Educational Apps For Kids",
              website: "https://elearningindustry.com/"
            },
            {
              image: "statics/games/appliances2.jpg",
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
              image: "statics/games/electronics1.jpg",
              desc: "12 Horrifyingly Violent Video Games",
              website: "https://www.rollingstone.com/"
            },
            {
              image: "statics/games/electronics2.jpg",
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
              image: "statics/games/gadget1.jpg",
              desc: "The most watched esports events of November 2019",
              website: "https://esportsinsider.com/"
            },
            {
              image: "statics/games/gadget2.jpg",
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
    var mySwiper = new Swiper(".games", {
      slidesPerView: 5,
      spaceBetween: 15,
      slidesOffsetAfter: 30
    });

    var mySwiper2 = new Swiper(".games-item", {
      slidesPerView: 2,
      spaceBetween: 15,
      slidesOffsetAfter: 30
    });
  }
};
</script>

<style lang="scss" scoped>
.hidden {
  display: none;
}
.swiper-container,
.games {
  width: 100%;
  padding-top: 1rem;
  overflow: hidden;
  border-bottom: 1px solid rgba(#fff, 0.1);
  // background-color: #202124;

  .swiper-wrapper {
    margin: 0 1rem;
    width: calc(100% - 2rem);
    .swiper-slide {
      // display: flex;
      // align-items: center;
      // justify-content: center;
      padding-bottom: 8px;
    }
  }

  .games__item {
    text-align: center;
    margin-top: 12px;

    .games__item-icon {
      img {
        border-radius: 8px;
        max-width: 100%;
        height: auto;
      }
    }

    .games__item-name {
      text-transform: capitalize;
      color: #fff;
      font-size: 0.75rem;
      text-align: center;
      margin-top: 4px;
    }
  }

  .tab-active {
    position: relative;

    &::after {
      content: "";
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      width: 100%;
      box-shadow: 0 0 0 1px $storya;
    }

    .games__item-name {
      color: $storya;
    }
  }
}
.games-panel {
  margin-top: 1rem;
  padding-bottom: 1.5rem;
  .games-wrapper {
    .games-item {
      width: 100%;

      .swiper-wrapper {
        margin: 0 1rem;
        width: calc(100% - 2rem);

        .swiper-slide {
          img {
            max-width: 100%;
            height: auto;
            border-radius: 5px;
          }

          .desc {
            line-height: 14px;
            color: rgba(#fff, 0.7);
            font-size: 12px;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
          }

          .website {
            color: #fff;
            font-size: 10px;
          }
        }
      }
    }
  }
}
</style>
