<template>
  <div>
    <div class="gateway-category-tab">
      <div class="section-title">TRAVEL DESTINATIONS</div>
      <div class="swiper-wrapper">
        <div
          class="swiper-slide"
          :class="dest.active ? 'tab-active' : ''"
          v-for="(dest, i) in destinations"
          :key="i"
          @click="selectActive(i)"
        >
          <div class="sub-category">
            <div class="sub-category__icon">
              <img class="swiper-lazy" :data-src="dest.icon" alt="" />
              <!-- <div class="swiper-lazy-preloader"></div> -->
              <q-spinner size="2em" color="white" class="swiper-preloader"></q-spinner>
            </div>
            <div class="sub-category__name">{{ dest.name }}</div>
          </div>
        </div>
      </div>
    </div>
    <div class="gateway-category-panel">
      <div
        class="gateway-category-panel__item "
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
            <img class="swiper-lazy" :data-src="item.image" alt="" />
            <div class="desc">{{ item.desc }}</div>
            <div class="website">{{ item.website }}</div>
            <!-- <div class="swiper-lazy-preloader"></div> -->
            <q-spinner size="2em" color="white" class="swiper-preloader"></q-spinner>
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
    var mySwiper = new Swiper(".gateway-category-tab", {
      slidesPerView: 5,
      spaceBetween: 15,
      slidesOffsetAfter: 30,
      preloadImages: false,
      lazy: {
        preloaderClass: "swiper-preloader"
      }
    });

    var mySwiper2 = new Swiper(".gateway-category-panel__item", {
      slidesPerView: 2,
      spaceBetween: 15,
      slidesOffsetAfter: 30,
      preloadImages: false,
      lazy: {
        preloaderClass: "swiper-preloader"
      }
    });
  }
};
</script>
