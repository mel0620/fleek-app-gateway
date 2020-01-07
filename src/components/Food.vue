<template>
  <div>
    <!-- <div class="row items-center justify-center">
      <div class="text-grey-5 q-mt-lg">Not available</div>
    </div> -->
    <div class="gateway-category-tab">
      <div class="section-title">Food</div>
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
              <img :src="dest.icon" alt="" />
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
            <img :src="item.image" alt="" />
            <div class="desc">{{ item.desc }}</div>
            <div class="website">{{ item.website }}</div>
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
          icon: "statics/food/food-all.jpg",
          name: "all",
          active: true,
          lists: [
            {
              image: "statics/food/food-buffet-1.jpg",
              desc: "23 of the Most Sulit Buffets in Manila",
              website: "https://ph.phonebooky.com/"
            },
            {
              image: "statics/food/food-dessert-2.jpg",
              desc: "THESE ARE THE 7 OF THE WEIRDEST DESSERTS FOUND ANYWHERE IN THE WORLD",
              website: "http://twistedfood.co.uk/"
            }
          ]
        },
        {
          icon: "statics/food/food-bread.jpg",
          name: "bread",
          active: false,
          lists: [
            {
              image: "statics/food/food-bread-1.jpg",
              desc: "The Best 10 Patisserie/Cake Shop in Manila",
              website: "https://en.yelp.com.ph/"
            },
            {
              image: "statics/food/food-bread-2.jpg",
              desc: "Dr Bergs Healthiest Bread In The World Recipe",
              website: "https://thewhoot.com/"
            }
          ]
        },
        {
          icon: "statics/food/food-buffet.jpg",
          name: "buffet",
          active: false,
          lists: [
            {
              image: "statics/food/food-buffet-1.jpg",
              desc: "23 of the Most Sulit Buffets in Manila",
              website: "https://ph.phonebooky.com/"
            },
            {
              image: "statics/food/food-buffet-2.jpg",
              desc: "2019 Buffet List: Top 18 Affordable Eat-All-You-Can Restaurants In Metro Manila",
              website: "https://www.ecomparemo.com/"
            }
          ]
        },
        {
          icon: "statics/food/food-desserts.jpg",
          name: "desserts",
          active: false,
          lists: [
            {
              image: "statics/food/food-dessert-1.jpg",
              desc: "5 Desserts To Make Based On Your Mood",
              website: "https://spoonuniversity.com/"
            },
            {
              image: "statics/food/food-dessert-2.jpg",
              desc: "THESE ARE THE 7 OF THE WEIRDEST DESSERTS FOUND ANYWHERE IN THE WORLD",
              website: "http://twistedfood.co.uk/"
            }
          ]
        },
        {
          icon: "statics/food/food-pasta.jpg",
          name: "pasta",
          active: false,
          lists: [
            {
              image: "statics/food/food-pasta-1.jpg",
              desc: "Italy's best traditional pasta dishes.",
              website: "https://www.greatitalianchefs.com/"
            },
            {
              image: "statics/food/food-pasta-2.jpg",
              desc: "5 Easy Pasta Dishes That Will Impress Your Friends and Family",
              website: "https://www.yummy.ph/"
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
      slidesOffsetAfter: 30
    });

    var mySwiper2 = new Swiper(".gateway-category-panel__item ", {
      slidesPerView: 2,
      spaceBetween: 15,
      slidesOffsetAfter: 30
    });
  }
};
</script>
