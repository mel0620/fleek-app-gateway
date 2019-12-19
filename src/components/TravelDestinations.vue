<template>
  <div>
    <div class="travel-destination">
      <div class="section-title">TRAVEL DESTINATIONS</div>
      <div class="swiper-wrapper">
        <div
          class="swiper-slide"
          :class="dest.active ? 'tab-active' : ''"
          v-for="(dest, i) in destinations"
          :key="i"
          @click="selectActive(i)"
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
        <div
          class="destination-item"
          v-for="(dest, index) in filterdDestinations"
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
      destinations: [
        {
          icon: "statics/destinations/all.jpg",
          name: "all",
          active: true,
          lists: [
            {
              image: "statics/destinations/resort-1.jpg",
              desc:
                "Go on an Exciting Adventure with a Day Tour Beach Access in Camayan Beach Resort, Subic",
              website: "https://www.metrodeal.com/"
            },
            {
              image: "statics/destinations/resort-2.jpg",
              desc:
                "2- or 4-Hour Samba Thrilla Pass with Beach Access in Samba Bluewater Resort, Olongapo City",
              website: "https://www.metrodeal.com/"
            }
          ]
        },
        {
          icon: "statics/destinations/hotel.jpg",
          name: "hotels",
          active: false,
          lists: [
            {
              image: "statics/destinations/hotel-1.jpg",
              desc:
                "Luxurious Accommodation with Breakfast Buffet, Transfers & More in Marco Polo Plaza Cebu",
              website: "https://www.metrodeal.com/"
            },
            {
              image: "statics/destinations/hotel-2.jpg",
              desc:
                "Accommodation with Breakfast Buffet & Massage for 2 Persons in Red Hotel Cubao, Quezon City",
              website: "https://www.metrodeal.com/"
            }
          ]
        },
        {
          icon: "statics/destinations/resort.jpg",
          name: "resorts",
          active: false,
          lists: [
            {
              image: "statics/destinations/resort-1.jpg",
              desc:
                "Go on an Exciting Adventure with a Day Tour Beach Access in Camayan Beach Resort, Subic",
              website: "https://www.metrodeal.com/"
            },
            {
              image: "statics/destinations/resort-2.jpg",
              desc:
                "2- or 4-Hour Samba Thrilla Pass with Beach Access in Samba Bluewater Resort, Olongapo City",
              website: "https://www.metrodeal.com/"
            }
          ]
        },
        {
          icon: "statics/destinations/transpo.jpg",
          name: "transpo",
          active: false,
          lists: [
            {
              image: "statics/destinations/transpo-1.jpg",
              desc:
                "Travel Conveniently with a 24-Hour Rental of Sedan in Automatic Transmission with Juzzr Car Rental",
              website: "https://www.metrodeal.com/"
            },
            {
              image: "statics/destinations/transpo-2.jpg",
              desc:
                "Travel with 12- or 24-Hour Car Rental with Unlimited Mileage in Luzon with Happy Mile Car Rentals",
              website: "https://www.metrodeal.com/"
            }
          ]
        },
        {
          icon: "statics/destinations/resto.jpg",
          name: "resto",
          active: false,
          lists: [
            {
              image: "statics/destinations/resto-1.jpg",
              desc:
                "P1000 worth of Food & Drinks at any Burgoo American Bar & Restaurant branches",
              website: "https://www.metrodeal.com/"
            },
            {
              image: "statics/destinations/resto-2.jpg",
              desc:
                "Indulge in an Eat-All-You-Can Lunch or Dinner Buffet at Midas Hotel in Midas Cafe, Pasay City",
              website: "https://www.metrodeal.com/"
            }
          ]
        }
      ]
    };
  },
  computed: {
    filterdDestinations() {
      return this.destinations.filter(res => res.active);
    }
  },
  methods: {
    selectActive(ind) {
      this.destinations.forEach(
        (dest, index) => (this.destinations[index].active = false)
      );
      this.destinations[ind].active = true;
    },
    openWebsite(link) {
      window.open(link, "_blank");
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
.hidden {
  display: none;
}
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
    position: relative;

    &::after {
      content: "";
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      width: 100%;
      box-shadow: 0 0 0 1px $storya;
    }

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
