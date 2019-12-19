<template>
  <div class="travel-destination">
    <div class="section-title">TRAVEL DESTINATIONS</div>
    <div class="swiper-wrapper">
      <div class="swiper-slide" v-for="(dest, i) in destinations" :key="i">
        <div class="travel-destination__item">
          <div class="travel-destination__item-icon">
            <img :src="dest.icon" alt="" />
          </div>
          <div class="travel-destination__item-name">{{ dest.name }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Swiper from "swiper";
import "swiper/css/swiper.min.css";

export default {
  data() {
    return {
      destinations: [
        {
          icon: "statics/all.jpg",
          name: "all"
        },
        {
          icon: "statics/hotel.jpg",
          name: "hotels"
        },
        {
          icon: "statics/resort.jpg",
          name: "Resorts"
        },
        {
          icon: "statics/transpo.jpg",
          name: "transpo"
        },
        {
          icon: "statics/resto.jpg",
          name: "resto"
        }
      ]
    };
  },
  mounted() {
    var mySwiper = new Swiper(".travel-destination", {
      slidesPerView: 5,
      spaceBetween: 15
    });
  }
};
</script>

<style lang="scss" scoped>
.swiper-container,
.travel-destination {
  width: 100%;
  padding-top: 1rem;
  border-bottom: 1px solid rgba(#fff, 0.1);
  // background-color: #202124;

  .section-title {
    padding: 0 14px;
  }

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

  .travel-destination__item {
    text-align: center;
    margin-top: 12px;

    .travel-destination__item-icon {
      img {
        border-radius: 8px;
        max-width: 100%;
        height: auto;
      }
    }

    .travel-destination__item-name {
      text-transform: capitalize;
      color: #fff;
      font-size: 0.75rem;
      text-align: center;
      margin-top: 4px;
    }
  }
}
</style>
