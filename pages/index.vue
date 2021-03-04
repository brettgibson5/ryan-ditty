<template>
  <div class="container">
    <header class="lg:absolute w-full left-0 md:flex hidden p-4 pb-0 flex justify-between items-center">
      <h1><img src="/img/logo.png" alt="Ryan Ditty" /></h1>
      <h2 class="lg:text-xl md:text-sm leading-tight uppercase text-right"><strong>A Celebration of Life</strong><br />March 6, 2021 // 3PM<br />C3 Los Angeles</h2>
    </header>
    <div class="relative">
      <Swiper :options="swiperOption" class="mx-auto relative" ref="mySwiper" @slideChange="changeSwiperIndex">
        <div class="swiper-slide flex items-center pb-20 px-8 pt-4" :key="banner" v-for="banner in banners">
          <!-- Render original HTML in server, render Swiper in browser (client) -->
          <img class="mx-auto max-h-full w-auto shadow-xl" :src="banner" />
        </div>
      </Swiper>
      <div class="absolute bottom-0 z-10 w-full flex items-center justify-center mb-2">
        <button class="swiper-prev bg-gray-400 rounded-full p-4 inline-block m-2" slot="button-prev" @click="prev()" :disabled="activeIndex === 0">
          <img src="/img/arrow.svg" class="w-4 pointer-events-none transform rotate-180" />
        </button>
        <div class="counter mx-4">{{ activeIndex + 1}} / {{banners.length}}</div>
        <button class="swiper-next bg-gray-400 rounded-full p-4 inline-block m-2" slot="button-next" @click="next()" :disabled="activeIndex + 1 === banners.length">
          <img src="/img/arrow.svg" class="w-4 pointer-events-none" />
        </button>
      </div>
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
      activeIndex: 0,
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
			this.$refs.mySwiper.$swiper.slidePrev();
		},
		next() {
			this.$refs.mySwiper.$swiper.slideNext();
		},
    changeSwiperIndex () {
      this.activeIndex = this.$refs.mySwiper.$swiper.activeIndex;
    }
	}
};
</script>

<style scoped>
h1 {
  width: 20vw;
  max-width: 300px;
}
h2 {
  color: #003471;
  letter-spacing: 3px;
}
.swiper-slide {
  height: 100vh;
  min-height: 400px;
}

.swiper-prev[disabled="disabled"],
.swiper-next[disabled="disabled"] {
  cursor: default;
  opacity: 0.4;
}
.counter {
  color: #00aeff;
}
@media only screen and (min-width: 768px) {
  .swiper-slide img {
    max-width: 600px;
  }
}

@media only screen and (max-width: 768px) {
  h2 {
    letter-spacing: 2px;
  }
}
@media only screen and (max-width: 640px) {
  .swiper-slide {
    height: 100vh;
  }
}
</style>
