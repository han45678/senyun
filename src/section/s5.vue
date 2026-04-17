<template>
  <section class="s5 relative overflow-hidden">
    <div class="container mx-auto relative z-10">
      <div class="header-content" data-aos="fade-up">
        <div class="brand-logo">
          <span class="logo-main">孕</span>
          <span class="logo-sub">永續基因</span>
        </div>
        <div class="bg-text-sustainability">SUSTAINABILITY</div>
        
        <h2 class="main-title">建築規劃 ‧ 永續綠建築</h2>
        <p class="desc">
          孕育家，也孕育未來，永續是寫給下一代的責任<br>
          從居家節能到森態呼吸，讓家成為最好的土壤
        </p>

        <div class="tags-container">
          <div class="tags-grid" ref="tagsGrid">
            <div 
              v-for="(item, index) in conceptData" 
              :key="index"
              class="tag-item"
              :class="{ 'active': activeIndex === index }"
              @click="slideTo(index)"
            >
              {{ item.tagName }}
            </div>
          </div>
        </div>
      </div>

      <div class="slider-wrapper" data-aos="fade">
        <swiper
          class="concept-swiper"
          :effect="'creative'"
          :creativeEffect="{
            prev: {
              translate: ['-80%', 0, -500],
              scale: 0.8,
              opacity: 0.6,
            },
            next: {
              translate: ['80%', 0, -500],
              scale: 0.8,
              opacity: 0.6,
            },
          }"
          :grabCursor="true"
          :slidesPerView="'auto'"
          :centeredSlides="true"
          :loop="true"
          :speed="1000"
          :autoplay="{
            delay: 5000,
            disableOnInteraction: false,
          }"
          :modules="modules"
          @swiper="onSwiper"
          @slideChange="onSlideChange"
        >
          <swiper-slide v-for="(item, index) in conceptData" :key="index" class="concept-slide">
            <div class="img-box">
              <img :src="item.img" :alt="item.tagName">
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import '@/assets/style/function.scss';

.s5 {
  width: 100%;
  padding: sizem(60) 0;
  background-color: #fff;
  position: relative;

  .header-content {
    padding: 0 sizem(30);
    position: relative;
    @media screen and (min-width: 768px) {
      padding: 0 size(150);
    }

    .brand-logo {
      display: flex;
      flex-direction: column;
      margin-bottom: sizem(20);
      .logo-main {
        font-size: sizem(45);
        color: #22ac38;
        line-height: 1;
        font-weight: bold;
      }
      .logo-sub {
        font-size: sizem(14);
        letter-spacing: 0.1em;
        color: #22ac38;
      }
      @media screen and (min-width: 768px) {
        margin-bottom: size(30);
        .logo-main { font-size: size(68); }
        .logo-sub { font-size: size(20); }
      }
    }

    .bg-text-sustainability {
      position: absolute;
      right: sizem(20);
      top: 0;
      font-size: sizem(32);
      font-weight: 900;
      color: transparent;
      -webkit-text-stroke: 1px rgba(34, 172, 56, 0.2);
      @media screen and (min-width: 768px) {
        font-size: size(100);
        right: size(150);
      }
    }

    .main-title {
      font-size: sizem(22);
      color: #22ac38;
      font-weight: bold;
      margin-bottom: sizem(10);
      @media screen and (min-width: 768px) {
        font-size: size(36);
        margin-bottom: size(15);
      }
    }

    .desc {
      font-size: sizem(14);
      color: #555;
      line-height: 1.8;
      margin-bottom: sizem(30);
      @media screen and (min-width: 768px) {
        font-size: size(20);
        margin-bottom: size(50);
      }
    }

    .tags-container {
      width: 100%;
      margin-bottom: sizem(40);
      @media screen and (min-width: 768px) {
        margin-bottom: size(60);
      }
    }

    .tags-grid {
      display: flex;
      overflow-x: auto;
      scroll-behavior: smooth;
      gap: sizem(10);
      // 隱藏捲軸
      &::-webkit-scrollbar { display: none; }
      scrollbar-width: none;

      .tag-item {
        flex: 0 0 auto;
        border: 1px solid #22ac38;
        border-radius: sizem(12);
        color: #22ac38;
        padding: sizem(8) sizem(20);
        font-size: sizem(15);
        cursor: pointer;
        transition: all 0.3s ease;

        &.active {
          background-color: #22ac38;
          color: #fff;
        }

        @media screen and (min-width: 768px) {
          padding: size(12) size(30);
          font-size: size(20);
          border-radius: size(10);
        }
      }
    }
  }

  .slider-wrapper {
    .concept-swiper {
      width: sizem(280); // 將 Swiper 容器限制為單張卡片寬度，確保 3D 計算準確
      margin: 0 auto; // 讓容器本身置中
      overflow: visible; // 讓左右卡片露出來
      @media screen and (min-width: 768px) {
        width: size(740);
      }
    }

    .concept-slide {
      width: 100%; // 卡片改為填滿 Swiper 容器


      .img-box {
        width: 100%;
        margin: 0 auto;
        aspect-ratio: 740 / 500; // 保持圖片比例
        border-radius: sizem(15);
        overflow: hidden;
        box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        // width: size(605);
        @media screen and (min-width: 768px) {
          border-radius: size(25);
          max-width: size(740); // 限制最大寬度
        }
        img {
          width: 100%;
          height: 100%;
          object-fit: cover;
          display: block;
        }
      }

      // .swiper-slide-active styles for width and opacity are no longer needed
    }
  }
}
</style>

<script setup>
import { ref, watch, nextTick } from 'vue';
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/effect-creative";
import { Autoplay, EffectCreative } from "swiper";

const modules = [Autoplay, EffectCreative];
const swiperRef = ref(null);
const activeIndex = ref(0);
const tagsGrid = ref(null);

// 數據定義
const conceptData = [
  { tagName: "銅級綠建築規劃", img: new URL("./s5/1.jpg", import.meta.url).href },
  { tagName: "20%EV礦石級匯流排", img: new URL("./s5/2.jpg", import.meta.url).href },
  { tagName: "EMS能源管理系統", img: new URL("./s5/3.jpg", import.meta.url).href },
  { tagName: "節能膠合玻璃", img: new URL("./s5/4.jpg", import.meta.url).href }
];

// 監聽 activeIndex，處理標籤自動置中
watch(activeIndex, (newVal) => {
  nextTick(() => {
    if (tagsGrid.value) {
      const activeEl = tagsGrid.value.children[newVal];
      if (activeEl) {
        const containerWidth = tagsGrid.value.offsetWidth;
        const itemLeft = activeEl.offsetLeft;
        const itemWidth = activeEl.offsetWidth;
        // 計算捲動位置使其置中
        tagsGrid.value.scrollLeft = itemLeft - (containerWidth / 2) + (itemWidth / 2);
      }
    }
  });
});

const onSwiper = (swiper) => {
  swiperRef.value = swiper;
};

const onSlideChange = (swiper) => {
  activeIndex.value = swiper.realIndex;
};

const slideTo = (index) => {
  if (swiperRef.value) {
    swiperRef.value.slideToLoop(index);
  }
};
</script>