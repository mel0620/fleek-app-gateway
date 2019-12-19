<template>
  <div>
    <div class="shop">
      <div class="section-title">SHOP</div>
      <div class="swiper-wrapper">
        <div
          class="swiper-slide"
          :class="dest.active ? 'tab-active' : ''"
          v-for="(dest, i) in shop"
          :key="i"
          @click="selectActive(i)"
        >
          <div class="shop__item">
            <div class="shop__item-icon">
              <img :src="dest.icon" alt="" />
            </div>
            <div class="shop__item-name">{{ dest.name }}</div>
          </div>
        </div>
      </div>
    </div>
    <div class="shop-panel">
      <div class="shop-wrapper">
        <div class="shop-item" v-for="(dest, index) in filterShop" :key="index">
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
              image: "statics/shop/appliances2.jpg",
              desc: "The 5 Best Affordable Luxury Appliance Brands",
              website: "https://blog.yaleappliance.com/"
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
    var mySwiper = new Swiper(".shop", {
      slidesPerView: 5,
      spaceBetween: 15,
      slidesOffsetAfter: 30
    });

    var mySwiper2 = new Swiper(".shop-item", {
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
.shop {
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

  .shop__item {
    text-align: center;
    margin-top: 12px;

    .shop__item-icon {
      img {
        border-radius: 8px;
        max-width: 100%;
        height: auto;
      }
    }

    .shop__item-name {
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

    .shop__item-name {
      color: $storya;
    }
  }
}
.shop-panel {
  margin-top: 1rem;
  padding-bottom: 1.5rem;
  .shop-wrapper {
    .shop-item {
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
