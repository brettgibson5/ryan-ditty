<template>
  <div class="container">
    <header class="sm:p-4 p-2 flex justify-between items-center mb-2">
      <h1><img src="/img/logo.png" class="h-16 md:h-32 mr-1" alt="Ryan Ditty" /></h1>
      <h2 class="md:text-xl sm:text-md text-sm leading-tight uppercase text-right"><strong>A Celebration of Life</strong><br />March 6, 2021 // 3PM<br />C3 Los Angeles</h2>
    </header>
    <Swiper :options="swiperOption" class="mx-auto relative" ref="swiper">
      <div class="swiper-slide flex items-center md:pb-12 pb-8 px-8 pt-2" :key="banner" v-for="banner in banners">
        <!-- Render original HTML in server, render Swiper in browser (client) -->
        <img class="mx-auto max-h-full w-auto shadow-xl" :src="banner" />
      </div>
    </Swiper>
    <div class="text-center">
      <button class="swiper-prev bg-gray-300 rounded-full p-4 inline-block m-2" slot="button-prev" @click="prev()">
        <img src="/img/arrow.svg" class="w-4 pointer-events-none transform rotate-180" />
      </button>
      <div class="swiper-pagination"></div>
      <button class="swiper-next bg-gray-300 rounded-full p-4 inline-block m-2" slot="button-next" @click="next()">
        <img src="/img/arrow.svg" class="w-4 pointer-events-none" />
      </button>
    </div>
  </div>
</template>
<script>
import { Swiper } from "vue-awesome-swiper";

export default {
  name: "Slider",
  components: { Swiper },
  data() {
    return {
      banners: ["/img/slide1.jpg", "/img/slide2.jpg", "/img/slide3.jpg", "/img/slide4.jpg"],
      swiperOption: {
        slidesPerView: 1,
        loop: false,
        pagination: {
          el: '.swiper-pagination',
          clickable: true
        },
        navigation: {
          nextEl: ".swiper-next",
          prevEl: ".swiper-prev",
        }
      },
    };
  },
  methods: {
		prev() {
			this.$refs.swiper.$swiper.slidePrev();
		},
		next() {
			this.$refs.swiper.$swiper.slideNext();
		}
	}
};
</script>

<style scoped>
h2 {
  color: #003471;
  letter-spacing: 3px;
}
.swiper-slide {
  height: calc(100vh - 240px);
  min-height: 400px;
}

@media only screen and (max-width: 768px) {
  h2 {
    letter-spacing: 2px;
  }
  .swiper-slide {
    height: calc(100vh - 160px);
  }
}

</style>
