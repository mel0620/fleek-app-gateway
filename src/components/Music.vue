<template>
  <div>
    <div class="gateway-category-tab">
      <div class="section-title">MUSIC</div>
      <div class="swiper-wrapper">
        <div
          class="swiper-slide"
          :class="dest.active ? 'tab-active' : ''"
          v-for="(dest, i) in music"
          :key="i"
          @click="selectActive(i)"
        >
          <div class="sub-category">
            <div class="sub-category__icon">
              <img :src="dest.icon" alt="" />
            </div>
            <div class="sub-category__name">{{ dest.name }}</div>
          </div>
        </div>
      </div>
    </div>
    <div class="gateway-category-panel">
      <div
        class="gateway-category-panel__item"
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
    var mySwiper = new Swiper(".gateway-category-tab", {
      slidesPerView: 5,
      spaceBetween: 15,
      slidesOffsetAfter: 30
    });

    var mySwiper2 = new Swiper(".gateway-category-panel__item", {
      slidesPerView: 2,
      spaceBetween: 15,
      slidesOffsetAfter: 30
    });
  }
};
</script>
