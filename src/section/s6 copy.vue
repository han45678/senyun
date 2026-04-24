<script setup>
import { ref, watch, nextTick, computed, getCurrentInstance } from 'vue';
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/css';
import 'swiper/css/effect-creative';
import { Autoplay, EffectCreative } from 'swiper';

const modules = [Autoplay, EffectCreative];
const swiperRef = ref(null);
const activeIndex = ref(0);
const tagsGrid = ref(null);

const globals = getCurrentInstance().appContext.config.globalProperties;
const isMobile = computed(() => globals.$isMobile());

// 數據定義
const conceptData = [
  {
    tagName: 'eTag+車牌辨識系統',
    img: new URL('./s6/1.jpg', import.meta.url).href
  },
  {
    tagName: '門禁影像監控系統',
    img: new URL('./s6/2.jpg', import.meta.url).href
  },
  {
    tagName: 'SYR雲端智控濾水',
    img: new URL('./s6/3.jpg', import.meta.url).href
  },
  {
    tagName: '玄關電子門鎖',
    img: new URL('./s6/4.jpg', import.meta.url).href
  },
  {
    tagName: '智能一鍵控光',
    img: new URL('./s6/5.jpg', import.meta.url).href
  }
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
        tagsGrid.value.scrollLeft =
          itemLeft - containerWidth / 2 + itemWidth / 2;
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
<!--
          :effect="'creative'"
        
          :creativeEffect="
            isMobile
              ? {
                  prev: {
                    translate: ['-20%', 0, -200] // 只露出 20%，其餘 80% 壓在後面
                  },
                  next: {
                    translate: ['20%', 0, -200]
                  }
                }
              : {
                  prev: {
                    translate: ['-80%', 0, -500] // 電腦版維持原樣
                  },
                  next: {
                    translate: ['80%', 0, -500]
                  }
                }
          "
          :autoplay="{
            delay: 5000,
            disableOnInteraction: false
          }"
        -->
<template>
  <section class="s6 relative overflow-hidden">
    <div class="container relative">
      <div class="title font-['Noto_Sans_TC']">
        <h2 data-aos="fade-up" data-aos-delay="0">
          <span>醞</span>
          智感生活
        </h2>
        <h3 data-aos="fade-up" data-aos-delay="200">
          智慧家居・數位守護
        </h3>
        <p data-aos="fade-up" data-aos-delay="400">
          一次次車道開啟，家知道你回來，一滴滴純淨的水，是家的輕柔問候<br />每一個智慧細節，讓您安心依靠，感受美好
        </p>
        <img class="en_title" src="./s5/en_title.svg" alt="en_title" data-aos="fade-up" data-aos-delay="600" />
      </div>
      <div class="header-content" data-aos="fade-up" data-aos-delay="800">
        <div class="tags-container">
          <div class="tags-grid" ref="tagsGrid">
            <div class="tag-item font-['Noto_Sans_TC']" style="border: none; cursor: default">
              GREEN FUTURE
            </div>
            <div v-for="(item, index) in conceptData" :key="index" class="tag-item font-['Noto_Sans_TC']"
              :class="{ active: activeIndex === index }" @click="slideTo(index)">
              {{ item.tagName }}
            </div>
          </div>
        </div>
      </div>

      <div class="slider-wrapper" data-aos="fade">
        <swiper
  class="concept-swiper"
  :grabCursor="true"
  :slidesPerView="'auto'"
  :centeredSlides="true"
  :loop="true"
  :speed="1000"
  :loopAdditionalSlides="2"
  :watchSlidesProgress="true"
  :modules="modules"
  @swiper="onSwiper"
  @slideChange="onSlideChange"
>
          <swiper-slide v-for="(item, index) in conceptData" :key="index" class="concept-slide">
  <div class="card-shadow">       <!-- ← 負責 box-shadow -->
    <div class="img-box">         <!-- ← 負責 overflow: hidden -->
      <img :src="item.img" :alt="item.tagName" />
    </div>
  </div>
</swiper-slide>
        </swiper>
      </div>
    </div>
    <div class="fs fs1" />
    <div class="fs fs2" />
    <div class="fs fs3" />
  </section>
</template>

<style lang="scss">
@import '@/assets/style/function.scss';

.s6 {
  .swiper-slide {
    transform: scale(0.65) translateY(40px);
    transition: transform 0.6s cubic-bezier(0.25, 0.46, 0.45, 0.94),
                box-shadow 0.6s ease;
    /* ❌ 不要在這層 overflow: hidden，會裁掉陰影 */
    /* ❌ 不要 opacity: 0，loop clone 會閃 */
    margin: 0 size(-200);
    opacity: 0;
    z-index: 1;

    @media screen and (min-width: 768px) {
      width: size(680);
      transform: scale(0.65) translateY(60px);
    }

    &.swiper-slide-prev,
    &.swiper-slide-next {
      z-index: 2;
      transform: scale(0.78) translateY(20px);
    opacity: 1;

      @media screen and (min-width: 768px) {
        transform: scale(0.78) translateY(30px);
      }

      .card-shadow {
        box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
      }
    }

    &.swiper-slide-active {
      transform: scale(1) translateY(0px);
      z-index: 5;
    opacity: 1;
      transition: transform 0.6s cubic-bezier(0.25, 0.46, 0.45, 0.94),
                  box-shadow 0.6s ease;

      .card-shadow {
        box-shadow: 0 20px 50px rgba(0, 0, 0, 0.35);
      }
    }

    /* ✅ loop clone 同步樣式，防止跳動 */
    &.swiper-slide-duplicate-active {
      transform: scale(1) translateY(0px);
      z-index: 5;

      .card-shadow {
        box-shadow: 0 20px 50px rgba(0, 0, 0, 0.35);
      }
    }

    &.swiper-slide-duplicate-prev,
    &.swiper-slide-duplicate-next {
      z-index: 2;
      transform: scale(0.78) translateY(20px);

      .card-shadow {
        box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
      }
    }
  }

  .slider-wrapper {
    padding: 0 sizem(30);
    transform: scale(0.9);
    padding-bottom: sizem(60);

    @media screen and (min-width: 768px) {
      transform: unset;
      padding: 0;
      padding-bottom: size(80);
    }

    .concept-swiper {
      width: sizem(280);
      margin: 0 auto;
      overflow: visible; /* ✅ swiper 容器要 visible，才看得到左右卡片 */

      @media screen and (min-width: 768px) {
        width: size(740);
      }
    }

    .concept-slide {
      width: 100%;

      /* ✅ 負責陰影，不能 overflow: hidden */
      .card-shadow {
        width: 100%;
        border-radius: sizem(5);
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
        transition: box-shadow 0.6s ease;

        @media screen and (min-width: 768px) {
          border-radius: size(25);
        }
      }

      /* ✅ 負責裁切圖片，不負責陰影 */
      .img-box {
        width: 100%;
        aspect-ratio: 740 / 500;
        border-radius: sizem(5);
        overflow: hidden; /* ← 只在這層裁切 */

        @media screen and (min-width: 768px) {
          border-radius: size(25);
        }

        img {
          width: 100%;
          height: 100%;
          object-fit: cover;
          display: block;
        }
      }
    }
  }
}
</style>
<style lang="scss" scoped>
@import '@/assets/style/function.scss';

.s6 {
  width: 100%;
  background-color: #fff;
  position: relative;
  background-position: center;
  background-size: 100% 100%;
  background-repeat: no-repeat;

  @media screen and (min-width: 768px) {
    background-image: url(./s6/bg.jpg);
  }

  .container {
    padding: 0 0;

    @media screen and (min-width: 768px) {
      max-width: size(1300);
      margin: 0 auto;
      padding: 0 size(30);
    }

    .title {
      text-align: center;
      margin-bottom: sizem(30);
      padding-top: sizem(100);

      @media screen and (min-width: 768px) {
        text-align: left;
        margin-bottom: size(40);
        padding-top: size(50);
      }

      h2 {
        color: #00ba00;
        font-weight: 400;
        font-size: sizem(14.23);
        line-height: 1;
        position: relative;
        padding-bottom: sizem(50);

        @media screen and (min-width: 768px) {
          padding-bottom: size(100);
          font-size: size(33);
          line-height: 0.7;
        }

        span {
          display: block;
          font-size: sizem(52.71);
          margin-bottom: sizem(10);

          @media screen and (min-width: 768px) {
            margin-bottom: 0;
            font-size: size(125);
            line-height: 1.3;
          }
        }

        &::before {
          content: '';
          width: sizem(0.5);
          height: sizem(40);
          background-color: #00ba00;
          position: absolute;
          left: 0;
          right: 0;
          margin: auto;
          bottom: sizem(-2.5);

          @media screen and (min-width: 768px) {
            width: size(0.5);
            height: size(80);
            right: auto;
            left: size(62);
            bottom: size(-5);
          }
        }
      }

      h3 {
        color: #00ba00;
        font-weight: 700;
        font-size: sizem(14);
        line-height: 1.2;
        margin: sizem(15) auto;
        writing-mode: vertical-lr;

        @media screen and (min-width: 768px) {
          writing-mode: unset;
          font-size: size(33);
          line-height: 1.3;
          margin: size(20) 0;
        }
      }

      p {
        font-weight: 400;
        font-size: sizem(12);
        line-height: 1.7;
        color: #666;

        @media screen and (min-width: 768px) {
          font-size: size(26);
          line-height: 1.3;
        }
      }

      .en_title {
        position: absolute;
        right: 0;
        left: 0;
        margin: auto;
        width: sizem(265);
        top: sizem(30);

        @media screen and (min-width: 768px) {
          right: 0;
          left: unset;
          top: size(80);
          width: size(845);
        }
      }
    }

    .header-content {
      padding: 0 sizem(60);
      position: relative;

      @media screen and (min-width: 768px) {
        padding: 0;
      }

      .tags-container {
        width: 100%;
        margin-bottom: sizem(20);

        @media screen and (min-width: 768px) {
          margin-bottom: size(60);
        }
      }

      .tags-grid {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: sizem(10);

        @media screen and (min-width: 768px) {
          grid-template-columns: repeat(3, 1fr);
          gap: size(30);
        }

        .tag-item {
          border: 0.34px solid #22ac38;
          border-radius: sizem(5);
          color: #22ac38;
          padding: sizem(8) sizem(5);
          font-size: sizem(9.94);
          cursor: pointer;
          transition: all 0.3s ease;
          text-align: center;
          font-weight: 400;
          line-height: 1;
          letter-spacing: 0;

          &.active {
            background-color: #22ac38;
            color: #fff;
          }

          @media screen and (min-width: 768px) {
            border-width: 0.89px;
            padding: size(12) 0;
            font-size: size(26);
            border-radius: size(10);
            line-height: 1.4;
          }
        }
      }
    }

  }

  .fs {
    border-radius: 50%;
    position: absolute;

    // 第一顆球
    &1 {
      position: absolute;
      width: size(264.88);
      height: size(264.88);
      top: size(176.78);
      left: size(1592.97);
      opacity: 1;
      background: linear-gradient(145deg,
          #52d300 14.09%,
          rgba(80, 205, 0, 0) 85.88%); // 延用前組漸層設定
      animation: floating 4.8s ease-in-out infinite;

      @media (max-width: 768px) {
        width: sizem(67.95);
        height: sizem(67.93);
        top: sizem(220.34);
        left: sizem(269.11);
      }
    }

    // 第二顆球
    &2 {
      position: absolute;
      width: size(264.88);
      height: size(264.88);
      top: size(550.95);
      left: size(89.01);
      opacity: 1;
      background: linear-gradient(322.79deg,
          #52d300 14.25%,
          rgba(80, 205, 0, 0) 85.62%);
      animation: floating 6.2s ease-in-out infinite;

      @media (max-width: 768px) {
        width: sizem(80.7);
        height: sizem(80.68);
        top: sizem(310.85);
        left: sizem(27.61);
      }
    }

    // 第三顆球 (電腦版隱藏)
    &3 {
      display: none;

      @media (max-width: 768px) {
        display: block;
        position: absolute;
        width: sizem(32.17);
        height: sizem(32.16);
        top: sizem(120.35);
        left: sizem(93.93);
        opacity: 1;
        background: linear-gradient(109.22deg,
            #52d300 10.73%,
            rgba(80, 205, 0, 0) 89.26%);
        animation: floating 5.2s ease-in-out infinite;
      }
    }
  }

  @keyframes floating {

    0%,
    100% {
      transform: translateY(0px);
    }

    50% {
      transform: translateY(-18px);
    }
  }
}
</style>
