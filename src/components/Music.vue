<template>
  <div>
    <div class="music">
      <div class="section-title">MUSIC</div>
      <div class="swiper-wrapper">
        <div
          class="swiper-slide"
          :class="dest.active ? 'tab-active' : ''"
          v-for="(dest, i) in music"
          :key="i"
          @click="selectActive(i)"
        >
          <div class="music__item">
            <div class="music__item-icon">
              <img :src="dest.icon" alt="" />
            </div>
            <div class="music__item-name">{{ dest.name }}</div>
          </div>
        </div>
      </div>
    </div>
    <div class="music-panel">
      <div class="music-wrapper">
        <div
          class="music-item"
          v-for="(dest, index) in filterMusic"
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
      music: [
        {
          icon: "statics/music/music-all.jpg",
          name: "all",
          active: true,
          lists: [
            {
              image: "statics/music/toy1.jpg",
              desc: "How to Help Your Child Make Friends",
              website: "https://www.parents.com/"
            },
            {
              image: "statics/music/appliances2.jpg",
              desc: "The 5 Best Affordable Luxury Appliance Brands",
              website: "https://blog.yaleappliance.com/"
            }
          ]
        },
        {
          icon: "statics/music/music-love.jpg",
          name: "love",
          active: false,
          lists: [
            {
              image: "statics/music/toy1.jpg",
              desc: "50 Best Love Songs to Add to Your Romance Playlist",
              website: "https://www.oprahmag.com/"
            },
            {
              image: "statics/music/toy2.jpg",
              desc: "The 40 Love Songs You Need to Close a Date",
              website: "https://www.esquire.com/"
            }
          ]
        },
        {
          icon: "statics/music/music-Rock.jpg",
          name: "Rock",
          active: false,
          lists: [
            {
              image: "statics/music/appliances1.jpg",
              desc: "150 Greatest Rock Songs of the 2000s",
              website: "https://rateyourmusic.com/"
            },
            {
              image: "statics/music/appliances2.jpg",
              desc: "The 100 most popular rock bands of all time ",
              website: "https://www.businessinsider.com/"
            }
          ]
        },
        {
          icon: "statics/music/music-pop.jpg",
          name: "pop",
          active: false,
          lists: [
            {
              image: "statics/music/electronics1.jpg",
              desc: "The 35 Best-Selling Pop Albums in American History",
              website: "https://www.mentalfloss.com/"
            },
            {
              image: "statics/music/electronics2.jpg",
              desc: "The Best Female Pop Singers Of 2019",
              website: "https://www.ranker.com/"
            }
          ]
        },
        {
          icon: "statics/music/music-metal.jpg",
          name: "metal",
          active: false,
          lists: [
            {
              image: "statics/music/gadget1.jpg",
              desc: "THE 25 MOST IMPORTANT METAL BANDS OF THE ’90S",
              website: "https://www.metalsucks.net/"
            },
            {
              image: "statics/music/gadget2.jpg",
              desc: "The 100 best metal songs of the 90s",
              website: "https://www.metalsucks.net/"
            }
          ]
        }
      ]
    };
  },
  computed: {
    filterMusic() {
      return this.music.filter(res => res.active);
    }
  },
  methods: {
    selectActive(ind) {
      this.music.forEach((dest, index) => (this.music[index].active = false));
      this.music[ind].active = true;
    },
    openWebsite(link) {
      window.open(link, "_blank");
    }
  },
  mounted() {
    var mySwiper = new Swiper(".music", {
      slidesPerView: 5,
      spaceBetween: 15,
      slidesOffsetAfter: 30
    });

    var mySwiper2 = new Swiper(".music-item", {
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
.music {
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

  .music__item {
    text-align: center;
    margin-top: 12px;

    .music__item-icon {
      img {
        border-radius: 8px;
        max-width: 100%;
        height: auto;
      }
    }

    .music__item-name {
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

    .music__item-name {
      color: $storya;
    }
  }
}
.music-panel {
  margin-top: 1rem;
  padding-bottom: 1.5rem;
  .music-wrapper {
    .music-item {
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
