<template>
  <div class="container">
    <header class="p-4 flex justify-between items-center">
      <h1><img src="/img/logo.png" class="h-16 md:h-32" alt="Ryan Ditty" /></h1>
      <h2 class="md:text-2xl text-md leading-tight uppercase xs:text-right"><strong>A Celebration of Life</strong><br />March 6, 2021 // 3PM<br />C3 Los Angeles</h2>
    </header>
    <div v-swiper="swiperOption" class="mx-auto relative" :loadtheme="false">
      <div class="swiper-wrapper">
        <div class="swiper-slide md:py-4 px-8" :key="banner" v-for="banner in banners">
          <!-- Render original HTML in server, render Swiper in browser (client) -->
          <img class="mx-auto max-h-full w-auto shadow-xl" :src="banner" />
        </div>
      </div>
      <div class="flex">
        <button class="swiper-prev bg-gray-300 rounded-full p-4 inline-block">
          <img src="/img/arrow.svg" class="w-4 transform rotate-180" />
        </button>
        <div class="swiper-pagination"></div>
        <button class="swiper-next bg-gray-300 rounded-full p-4 inline-block">
          <img src="/img/arrow.svg" class="w-4" />
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import { directive } from "vue-awesome-swiper";

export default {
  name: "Slider",
  directives: {
    swiper: directive,
  },
  data() {
    return {
      banners: ["/img/slide1.jpg", "/img/slide2.jpg", "/img/slide3.jpg", "/img/slide4.jpg"],
      swiperOption: {
        slidesPerView: 1,
        loop: false,
        pagination: {
          el: '.swiper-pagination',
          type: 'bullets',
        },
        navigation: {
          nextEl: ".swiper-next",
          prevEl: ".swiper-prev",
        }
      },
    };
  },
};
</script>

<style scoped>
h2 {
  color: #003471;
}
.swiper-slide {
  height: calc(100vh - 10rem);
}

@media only screen and (max-width: 768px) {
  .swiper-slide {
    height: calc(100vh - 6rem);
  }
}

</style>
