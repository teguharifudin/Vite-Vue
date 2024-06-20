<script>
import { Swiper, SwiperSlide } from "swiper/vue";
import { FreeMode, Pagination, Autoplay } from "swiper/modules";

export default {
  components: {
    Swiper,
    SwiperSlide,
  },

  setup() {
    return {
      modules: [Autoplay, FreeMode, Pagination],
      n: 1,
    };
  },
};
</script>

<template>
  <div
    class="relative bg-gray-50 pt-16 pb-20 px-4 sm:px-6 lg:pt-24 lg:pb-28 lg:px-8"
  >
    <div class="absolute inset-0">
      <div class="bg-white h-1/3 sm:h-2/3" />
    </div>
    <div class="relative max-w-7xl mx-auto">
      <div class="text-center">
        <h2
          class="text-3xl tracking-tight font-extrabold text-gray-900 sm:text-4xl"
        >
          Explore Latest Projects
        </h2>
        <p class="mt-3 max-w-2xl mx-auto text-xl text-gray-500 sm:mt-4">
          There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration, by injected humour, or new randomised words.
        </p>
      </div>
      <div class="mt-12">
        <swiper
          :slidesPerView="3"
          :spaceBetween="30"
          :autoplay="{
            delay: 2500,
            disableOnInteraction: false,
          }"
          :loop="true"
          :pagination="{
            clickable: true,
            el: '.swip-paginate',
          }"
          :modules="modules"
          effect="fade"
          class="mySwiper"
        >
          <template v-for="n in 10">
            <swiper-slide>
              <div class="shadow-lg p-2 rounded-lg bg-gray-200">
                <img
                  class="rounded"
                  src="https://picsum.photos/200/280"
                  alt=""
                  loading="lazy"
                />
              </div>
            </swiper-slide>
          </template>
        </swiper>
      </div>
    </div>
    <div class="flex justify-center text-center py-6 max-w-7xl mx-auto">
      <div class="swip-paginate"></div>
    </div>
  </div>
</template>