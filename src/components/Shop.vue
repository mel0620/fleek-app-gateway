<template>
  <div>
    <div class="gateway-category-tab">
      <div class="section-title">SHOP</div>
      <div class="swiper-wrapper">
        <div
          class="swiper-slide"
          :class="dest.active ? 'tab-active' : ''"
          v-for="(dest, i) in shop"
          :key="i"
          @click="selectActive(i)"
        >
          <div class="sub-category">
            <div class="sub-category__icon">
              <img class="swiper-lazy" :data-src="dest.icon" alt="" />
              <q-spinner size="2em" color="white" class="swiper-preloader"></q-spinner>
            </div>
            <div class="sub-category__name">{{ dest.name }}</div>
          </div>
        </div>
      </div>
    </div>
    <div class="gateway-category-panel">
      <div
        class="gateway-category-panel__item"
        v-for="(dest, index) in filterShop"
        :key="index"
      >
        <div class="swiper-wrapper">
          <div
            class="swiper-slide"
            v-for="(item, ind) in dest.lists"
            :key="ind"
            @click="openWebsite(item.website)"
          >
            <img class="swiper-lazy" :src="item.image" alt="" />
            <div class="desc">{{ item.desc }}</div>
            <div class="website">{{ item.website }}</div>
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
      shop: [
        {
          icon: "statics/shop/shop-all.jpg",
          name: "all",
          active: true,
          lists: [
            {
              image: "statics/shop/toy1.jpg",
              desc: "How to Help Your Child Make Friends",
              website: "https://www.parents.com/"
            },
            {
            image: "statics/shop/electronics2.jpg",
              desc:
                "Zuken unveils high-speed features for Internet-connected PCB design",
              website: "http://www.newelectronics.co.uk/"
            }
          ]
        },
        {
          icon: "statics/shop/shop-appliances.jpg",
          name: "appliances",
          active: false,
          lists: [
            {
              image: "statics/shop/appliances1.jpg",
              desc: "Most Reliable Appliance Brands for 2019",
              website: "https://blog.yaleappliance.com/"
            },
            {
              image: "statics/shop/appliances2.jpg",
              desc: "The 5 Best Affordable Luxury Appliance Brands",
              website: "https://blog.yaleappliance.com/"
            }
          ]
        },
        {
          icon: "statics/shop/shop-electronics.jpg",
          name: "electronics",
          active: false,
          lists: [
            {
              image: "statics/shop/electronics1.jpg",
              desc:
                "Reorganizing a computer chip: Transistors can now both process and store information",
              website: "https://www.sciencedaily.com/"
            },
            {
              image: "statics/shop/electronics2.jpg",
              desc:
                "Zuken unveils high-speed features for Internet-connected PCB design",
              website: "http://www.newelectronics.co.uk/"
            }
          ]
        },
        {
          icon: "statics/shop/shop-gadgets.jpg",
          name: "gadgets",
          active: false,
          lists: [
            {
              image: "statics/shop/gadget1.jpg",
              desc: "Best gaming phones 2019: T3's best gaming phone picks",
              website: "https://www.t3.com/"
            },
            {
              image: "statics/shop/gadget2.jpg",
              desc: "Best Cheap Android Phones in 2019",
              website: "https://www.androidcentral.com/"
            }
          ]
        },
        {
          icon: "statics/shop/shop-toys.jpg",
          name: "toys",
          active: false,
          lists: [
            {
              image: "statics/shop/toy1.jpg",
              desc: "How to Help Your Child Make Friends",
              website: "https://www.parents.com/"
            },
            {
              image: "statics/shop/toy2.jpg",
              desc: "How to Buy Safe Toys",
              website: "https://www.healthychildren.org/"
            }
          ]
        }
      ]
    };
  },
  computed: {
    filterShop() {
      return this.shop.filter(res => res.active);
    }
  },
  methods: {
    selectActive(ind) {
      this.shop.forEach((dest, index) => (this.shop[index].active = false));
      this.shop[ind].active = true;
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
