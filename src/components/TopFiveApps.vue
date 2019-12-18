<template>
  <div>
    <div class="top-five-apps">
      <div class="section-title">TOP 5 APPS</div>
      <div class="swiper-wrapper">
        <div
          class="swiper-slide"
          @click="showAppDetails(i)"
          v-for="(app, i) in apps"
          :key="i"
        >
          <div class="app-icon">
            <img :src="app.icon" :alt="app.name" />
          </div>
        </div>
      </div>
    </div>
    <q-dialog
      maximized
      transition-show="fade"
      transition-hide="fade"
      v-model="dialog"
    >
      <q-card style="background-color: #202124">
        <button
          class="app-back"
          style="margin-left: 12px"
          @click="dialog = false"
        >
          <q-icon
            size="20px"
            color="white"
            name="mdi-keyboard-backspace"
          ></q-icon>
          <div class="app-back__label">Back</div>
        </button>
        <div>
          <!-- <img :src="" alt="" /> -->
        </div>
      </q-card>
    </q-dialog>
  </div>
</template>

<script>
import Swiper from "swiper";
import "swiper/css/swiper.min.css";

export default {
  name: "top-five-apps",
  data() {
    return {
      dialog: false,
      details: [],
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
  methods: {
    showAppDetails(id) {
      this.dialog = true;
    }
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
