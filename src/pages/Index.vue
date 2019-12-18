<template>
  <div class="app-gateway" :style="`--background: url('${bg_image}')`">
    <q-page-container>
      <q-page>
        <div class="app-gateway__content">
          <!-- <lorem></lorem> -->
        </div>
        <q-page-sticky expand position="top" style="z-index: 10">
          <div class="categories-tab">
            <div class="swiper-wrapper">
              <div class="swiper-slide" v-for="(cat, i) in categories" :key="i">
                <div class="categories-tab__item">
                  <div class="categories-tab__item-icon">
                    <img width="22" :src="cat.icon" alt="" />
                  </div>
                  <div class="categories-tab__item-name">{{ cat.name }}</div>
                </div>
              </div>
            </div>
          </div>
        </q-page-sticky>
      </q-page>
    </q-page-container>
  </div>
</template>

<script>
import Swiper from "swiper";
import "swiper/css/swiper.min.css";
import Lorem from "../components/Lorem";

export default {
  name: "PageIndex",
  components: {
    Lorem
  },
  data() {
    return {
      categories_tab: "mail",
      bg_image: "statics/get-started.jpg",
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
  mounted() {
    var mySwiper = new Swiper(".categories-tab", {
      slidesPerView: 5
    });
  }
};
</script>

<style lang="scss">
.app-gateway {
  position: relative;
  min-height: 100vh;
  --background: #fff;
  background-color: #111010;

  &::before {
    content: " ";
    background: linear-gradient(rgba(#000, 0.4), rgba(#000, 0.4));
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 2;
  }

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

  .categories-tab {
    margin-top: 1rem;
    border-bottom: 1px solid rgba(#fff, 0.1);

    .swiper-wrapper {
      padding: 0 12px 8px;

      .swiper-slide {
        display: flex;
        align-items: center;
        justify-content: center;
      }
    }

    &__item {
      text-align: center;

      &-icon {
        background-color: #f59b20;
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

      &-name {
        text-transform: capitalize;
        color: #fff;
        font-size: 0.75rem;
        text-align: center;
        width: 45px;
        margin-top: 4px;
      }
    }
  }

  &__content {
    padding-top: 60px;
    position: relative;
    z-index: 3;
  }
}
</style>
