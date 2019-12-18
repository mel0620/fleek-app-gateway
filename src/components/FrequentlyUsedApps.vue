<template>
  <div class="frequenly-used-apps">
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
          icon: "statics/fb.svg",
          name: "facebook"
        },
        {
          icon: "statics/ig.svg",
          name: "instagram"
        }
      ]
    };
  },
  mounted() {
    var mySwiper = new Swiper(".frequenly-used-apps", {
      slidesPerView: 5
    });
  }
};
</script>
