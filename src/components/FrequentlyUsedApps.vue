<template>
  <div class="frequently-used-apps">
    <div class="section-title">FREQUENTLY USED APPS</div>
    <div class="swiper-wrapper">
      <div class="swiper-slide" v-for="(app, i) in apps" :key="i">
        <div class="app-icon">
          <img :src="app.icon" :alt="app.name" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Swiper from "swiper";
import "swiper/css/swiper.min.css";

export default {
  name: "frequently-used-apps",
  data() {
    return {
      apps: [
        {
          icon: "statics/fb.svg",
          name: "facebook"
        },
        {
          icon: "statics/messenger.svg",
          name: "messenger"
        },
        {
          icon: "statics/tiktok.svg",
          name: "tiktok"
        },
        {
          icon: "statics/grab.svg",
          name: "grab"
        },
        {
          icon: "statics/spotify.svg",
          name: "spotify"
        },
        {
          icon: "statics/ig.svg",
          name: "instagram"
        }
      ]
    };
  },
  mounted() {
    var mySwiper = new Swiper(".frequently-used-apps", {
      slidesPerView: 6,
      spaceBetween: 15
    });
  }
};
</script>

<style lang="scss">
.frequently-used-apps {
  padding: 0 14px;
  .swiper-wrapper {
    .swiper-slide {
      .app-icon {
        margin-top: 8px;
        img {
          border-radius: 8px;
        }
      }
    }
  }
}
</style>
