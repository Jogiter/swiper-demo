<template>
  <swiper
    :slidesPerView="2"
    :centeredSlides="true"
    :centeredSlidesBounds="false"
    :spaceBetween="20"
    @slideChange="slideChange"
    :pagination="{
      clickable: true,
    }"
    :modules="modules"
    :setWrapperSize="true"
    :autoplay="{
      delay: 2500,
      disableOnInteraction: false,
    }"
  >
    <swiper-slide v-for="(text, i) of texts" :key="i" v-slot="{ isActive }">
      <p
        class="
          h-full
          mx-auto
          rounded-2xl
          flex-shrink-0
          text-[14px]
          lg:w-[496px] lg:text-[20px]
          leading-[normal]
          font-normal
          dark:text-gray-default
          p-6
          mb-0
          lg:mb-5
          !flex
          items-center
          snap-always snap-center
          transition-all
          duration-300
          text-center
          lg:text-left
        "
        :class="isActive ? 'bg-[#e0eaff]' : 'bg-[#F2F3F5]'"
      >
        {{ text }}
      </p>
    </swiper-slide>
    <div
      class="
        mt-10
        dark:bg-dark-100
        bg-[#F5F6F7BF]
        rounded-[30px]
        relative
        w-[243px]
        mx-auto
        h-1
        lg:w-1.5 lg:h-[540px]
      "
    >
      <span
        class="
          absolute
          left-0
          right-0
          top-0
          w-1/4
          h-full
          lg:h-1/4 lg:w-full
          bg-[#3754E5]
          rounded-[30px]
          transition-all
          duration-300
        "
        :class="{
          '': active === 0,
          'left-1/4 lg:top-1/4': active === 1,
          'left-1/2 lg:top-1/2': active === 2,
          'left-3/4 lg:top-3/4': active === 3,
        }"
      ></span>
    </div>
  </swiper>
</template>
<script>
// Import Swiper Vue.js components
import { ref } from 'vue';
import { Swiper, SwiperSlide } from 'swiper/vue';

// Import Swiper styles
import 'swiper/css';

import 'swiper/css/pagination';
import 'swiper/css/autoplay';

import './style.css';

// import required modules
import { Pagination, Autoplay } from 'swiper/modules';

export default {
  components: {
    Swiper,
    SwiperSlide,
  },
  setup() {
    const active = ref(0);
    const slideChange = (swiper) => {
      console.log(swiper.activeIndex);
      active.value = swiper.activeIndex;
    };

    return {
      active,
      modules: [
        // Pagination,
        Autoplay,
      ],
      slideChange,
      texts: [
        'Support multi-chain, multi-currency decentralized on-chain receipt and payment service',
        'Use smart contract accounts to realize merchant wallet logic and reduce manual verification costs',
        'Provide multi-company, multi-account enterprise management services',
        'Customer independent collection and withdrawal account to avoid confusion in customer withdrawals and reduce manual verification costs',
      ],
    };
  },
};
</script>
