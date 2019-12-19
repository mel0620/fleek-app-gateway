<template>
  <div class="frequently-used-apps">
    <div class="section-title">FREQUENTLY USED APPS</div>
    <div class="swiper-wrapper">
      <div
        class="swiper-slide"
        v-for="(app, i) in apps"
        :key="i"
        @click="showAppDetails(i, app)"
      >
        <div class="app-icon">
          <img :src="app.icon" :alt="app.name" />
        </div>
      </div>
    </div>
    <q-dialog
      maximized
      transition-show="fade"
      transition-hide="fade"
      v-model="dialog"
    >
      <q-card class="q-pb-lg" style="background-color: #202124">
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
        <div class="app-details">
          <div class="app-info">
            <div class="app-info__label">You are opening</div>
            <img :src="details.icon" alt="" />
            <div class="app-name">{{ details.name }}</div>
          </div>
          <div class="add-space">
            <img :src="details.add" :alt="details.add" />
          </div>
          <button v-ripple class="btn-app-continue">
            <div>CONTINUE TO {{ details.name }}</div>
            <div class="points">and receive 10 Points</div>
          </button>
        </div>
      </q-card>
    </q-dialog>
  </div>
</template>

<script>
import Swiper from "swiper";
import "swiper/css/swiper.min.css";

export default {
  name: "frequently-used-apps",
  data() {
    return {
      dialog: false,
      details: {},
      apps: [
        {
          icon: "statics/apps/fb.svg",
          name: "facebook",
          add:
            "https://sm.mashable.com/t/mashable_sea/news/k/kfc-to-add/kfc-to-add-fried-chicken-wings-to-its-menu_mtfz.960.png"
        },
        {
          icon: "statics/apps/messenger.svg",
          name: "messenger",
          add:
            "https://the828.sagacom.com/wp-content/blogs.dir/191/files/2018/06/kfc.png"
        },
        {
          icon: "statics/apps/tiktok.svg",
          name: "tiktok",
          add:
            "https://cdn.phonebooky.com/blog/wp-content/uploads/2019/10/18135103/73153510_2943101579051935_600562575465250816_o.jpg"
        },
        {
          icon: "statics/apps/grab.svg",
          name: "grab",
          add:
            "http://tripkoto.salezoneph.com/wp-content/uploads/2019/04/FB_IMG_1555028690880.jpg"
        },
        {
          icon: "statics/apps/spotify.svg",
          name: "spotify",
          add:
            "https://the828.sagacom.com/wp-content/blogs.dir/191/files/2018/06/kfc.png"
        },
        {
          icon: "statics/apps/ig.svg",
          name: "instagram",
          add:
            "https://cdn.greatdeals.com.sg/wp-content/uploads/2018/03/02002116/kfc-mozzarella-zinger-burger-march-2018.jpg"
        }
      ]
    };
  },
  methods: {
    showAppDetails(id, app) {
      this.dialog = true;
      this.details.icon = app.icon;
      this.details.name = app.name;
      this.details.add = app.add;
    }
  },
  mounted() {
    var mySwiper = new Swiper(".frequently-used-apps", {
      slidesPerView: 6,
      spaceBetween: 15,
      slidesOffsetAfter: 30
    });
  }
};
</script>

<style lang="scss">
.frequently-used-apps {
  width: 100%;
  overflow: hidden;
  .swiper-wrapper {
    margin: 0 1rem;
    width: calc(100% - 2rem);
    .swiper-slide {
      .app-icon {
        margin-top: 8px;
        img {
          border-radius: 8px;
          max-width: 100%;
          height: auto;
        }
      }
    }
  }
}
</style>
