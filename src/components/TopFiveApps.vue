<template>
  <div>
    <div class="top-five-apps">
      <div class="section-title">TOP 5 APPS</div>
      <div class="swiper-wrapper">
        <div
          class="swiper-slide"
          @click="showAppDetails(i, app)"
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
  name: "top-five-apps",
  data() {
    return {
      dialog: false,
      details: {},
      apps: [
        {
          icon: "statics/apps/tripadvisor.svg",
          name: "tripadvisor",
          add:
            "https://image.cnbcfm.com/api/v1/image/106008977-156267514025104113-4_tacos_pr_images_cr.jpg?v=1562675184"
        },
        {
          icon: "statics/apps/expedia.svg",
          name: "expedia",
          add:
            "https://assets1.csnews.com/files/styles/content_sm/s3/2018-02/McDonalds%20Happy%20Meal.jpg?itok=1ng0cLST"
        },
        {
          icon: "statics/apps/pinterest.svg",
          name: "pinterest",
          add:
            "https://www.qsrmagazine.com/sites/default/files/styles/story_page/public/news-image/kfc-adds-fried-wings-menus-nationwide.jpg?itok=Z5J5ZZ3q"
        },
        {
          icon: "statics/apps/viber.svg",
          name: "viber",
          add: "https://media.graytvinc.com/images/810*450/KFC30.jpg"
        },
        {
          icon: "statics/apps/whatsapp.svg",
          name: "whatsapp",
          add:
            "https://cdn.rttnews.com/articleimages/ustopstories/2019/november/popeyeschickensandwich-nov04-lt.jpg"
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
    var mySwiper = new Swiper(".top-five-apps", {
      slidesPerView: 5,
      spaceBetween: 15,
      slidesOffsetAfter: 30
    });
  }
};
</script>

<style lang="scss">
.top-five-apps {
  width: 100%;
  margin-top: 1rem;
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

.app-details {
  .app-info {
    text-align: center;
    margin: 1rem;

    &__label {
      color: white;
    }

    img {
      max-width: 100%;
      height: auto;
      width: 50px;
      margin-top: 1rem;
      border-radius: 5px;
    }

    .app-name {
      text-transform: capitalize;
      color: white;
    }
  }
  .add-space {
    margin: 1.5rem 1rem;
    // border: 2px solid rgba(#fff, 0.1);
    width: calc(100% - 2rem);
    height: 50%;
    display: flex;
    align-items: center;

    img {
      max-width: 100%;
      height: auto;
      margin: auto;
      object-fit: contain;
    }
  }
  .btn-app-continue {
    text-align: center;
    margin: 0 1rem;
    width: calc(100% - 2rem);
    border-radius: 5px;
    background-color: $storya;
    line-height: 12px;
    padding: 10px 12px;
    border: 0;
    outline: none;
    position: relative;

    div:first-child {
      text-transform: uppercase;
      color: white;
      font-size: 0.875rem;
    }

    div.points {
      color: white;
      font-size: 0.75rem;
      opacity: 0.6;
    }
  }
}
</style>
