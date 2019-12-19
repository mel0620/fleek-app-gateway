<template>
  <div>
    <div class="travel-destination">
      <div class="section-title">TRAVEL DESTINATIONS</div>
      <div class="swiper-wrapper">
        <div
          class="swiper-slide tab-active"
          v-for="(dest, i) in destinations"
          :key="i"
          @click="tab_active = dest.name"
        >
          <div class="travel-destination__item">
            <div class="travel-destination__item-icon">
              <img :src="dest.icon" alt="" />
            </div>
            <div class="travel-destination__item-name">{{ dest.name }}</div>
          </div>
        </div>
      </div>
    </div>
    <div class="destinations-panel">
      <div class="destinations-wrapper">
        <div class="destination-item">
          <div class="swiper-wrapper">
            <div class="swiper-slide">
              <img src="statics/destinations/hotel-1.jpg" alt="" />
              <div class="desc">
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Eaque,
                rerum.
              </div>
              <div class="website">metrodeal.com</div>
            </div>
            <div class="swiper-slide">
              <img src="statics/destinations/hotel-2.jpg" alt="" />
              <div class="desc">
                Lorem ipsum dolor sit amet consectetur adipisicing elit. Eaque,
                rerum.
              </div>
              <div class="website">metrodeal.com</div>
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
  data() {
    return {
      tab_active: "all",
      destinations: [
        {
          icon: "statics/destinations/all.jpg",
          name: "all",
          lists: [
            {
              image: "statics/destinations/hotel-1.jpg",
              desc: "Lorem ipsum dolor sir amet consectetuer adiphising init",
              website: "metrodeal.com"
            },
            {
              image: "statics/destinations/hotel-2.jpg",
              desc: "Lorem ipsum dolor sir amet consectetuer adiphising init",
              website: "metrodeal.com"
            },
            {
              image: "statics/destinations/hotel-1.jpg",
              desc: "Lorem ipsum dolor sir amet consectetuer adiphising init",
              website: "metrodeal.com"
            },
            {
              image: "statics/destinations/hotel-2.jpg",
              desc: "Lorem ipsum dolor sir amet consectetuer adiphising init",
              website: "metrodeal.com"
            }
          ]
        },
        {
          icon: "statics/destinations/hotel.jpg",
          name: "hotels",
          lists: [
            {
              image: "statics/destinations/hotel-1.jpg",
              desc: "Lorem ipsum dolor sir amet consectetuer adiphising init",
              website: "metrodeal.com"
            },
            {
              image: "statics/destinations/hotel-2.jpg",
              desc: "Lorem ipsum dolor sir amet consectetuer adiphising init",
              website: "metrodeal.com"
            }
          ]
        },
        {
          icon: "statics/destinations/resort.jpg",
          name: "resorts",
          lists: [
            {
              image: "statics/destinations/resort-1.jpg",
              desc: "Lorem ipsum dolor sir amet consectetuer adiphising init",
              website: "metrodeal.com"
            },
            {
              image: "statics/destinations/resort-2.jpg",
              desc: "Lorem ipsum dolor sir amet consectetuer adiphising init",
              website: "metrodeal.com"
            }
          ]
        },
        {
          icon: "statics/destinations/transpo.jpg",
          name: "transpo",
          lists: [
            {
              image: "statics/destinations/transpo-1.jpg",
              desc: "Lorem ipsum dolor sir amet consectetuer adiphising init",
              website: "metrodeal.com"
            },
            {
              image: "statics/destinations/transpo-2.jpg",
              desc: "Lorem ipsum dolor sir amet consectetuer adiphising init",
              website: "metrodeal.com"
            }
          ]
        },
        {
          icon: "statics/destinations/resto.jpg",
          name: "resto",
          lists: [
            {
              image: "statics/destinations/resto-1.jpg",
              desc: "Lorem ipsum dolor sir amet consectetuer adiphising init",
              website: "metrodeal.com"
            },
            {
              image: "statics/destinations/resto-2.jpg",
              desc: "Lorem ipsum dolor sir amet consectetuer adiphising init",
              website: "metrodeal.com"
            }
          ]
        }
      ]
    };
  },
  computed: {
    filterdDestinations() {
      let data = null;
      this.destinations.filter(res => {
        if (this.tab_active != "all") {
          if (res.name == this.tab_active) {
            return true;
          }
        } else {
          return true;
        }
      });
      return this.destinations.lists;
    }
  },
  mounted() {
    var mySwiper = new Swiper(".travel-destination", {
      slidesPerView: 5,
      spaceBetween: 15,
      slidesOffsetAfter: 30
    });

    var mySwiper2 = new Swiper(".destination-item", {
      slidesPerView: 2,
      spaceBetween: 15,
      slidesOffsetAfter: 30
    });
  }
};
</script>

<style lang="scss" scoped>
.swiper-container,
.travel-destination {
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

  .tab-active {
    border-bottom: 1px solid $storya;

    .travel-destination__item-name {
      color: $storya;
    }
  }
}
.destinations-panel {
  margin-top: 1rem;
  padding-bottom: 1.5rem;
  .destinations-wrapper {
    .destination-item {
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
