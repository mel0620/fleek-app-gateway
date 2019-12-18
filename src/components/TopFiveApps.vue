<template>
  <div class="top-five-apps">
    <div class="section-title">TOP 5 APPS</div>
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
  name: "Frequently Used Apps",
  data() {
    return {
      apps: [
        {
          icon: "statics/tripadvisor.svg",
          name: "tripadvisor"
        },
        {
          icon: "statics/expedia.svg",
          name: "expedia"
        },
        {
          icon: "statics/pinterest.svg",
          name: "pinterest"
        },
        {
          icon: "statics/grab.svg",
          name: "grab"
        },
        {
          icon: "statics/spotify.svg",
          name: "spotify"
        }
      ]
    };
  },
  mounted() {
    var mySwiper = new Swiper(".top-five-apps", {
      slidesPerView: 5,
      spaceBetween: 15
    });
  }
};
</script>

<style lang="scss">
.top-five-apps {
  margin-top: 1rem;
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
