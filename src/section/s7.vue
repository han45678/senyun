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
    tagName: '銅級綠建築規劃',
    img: new URL('./s5/1.jpg', import.meta.url).href
  },
  {
    tagName: '20%EV礦石級匯流排',
    img: new URL('./s5/2.jpg', import.meta.url).href
  },
  {
    tagName: 'EMS能源管理系統',
    img: new URL('./s5/3.jpg', import.meta.url).href
  },
  { tagName: '節能膠合玻璃', img: new URL('./s5/4.jpg', import.meta.url).href }
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

<template>
  <section class="s5 relative overflow-hidden">
    <div class="container relative">
      <div class="title font-['Noto_Sans_TC']">
        <h2>
          <span>孕</span>
          永續基因
        </h2>
        <h3>建築規劃・永續綠建築</h3>
        <p>
          孕育家，也孕育未來，永續是寫給下一代的責任<br />從居家節能到森態呼吸，讓家成為最好的土壤
        </p>
      </div>
      <div class="header-content">
        <div class="tags-container">
          <div
            class="tags-grid"
            ref="tagsGrid"
          >
            <div
              v-for="(item, index) in conceptData"
              :key="index"
              class="tag-item font-['Noto_Sans_TC']"
              :class="{ active: activeIndex === index }"
              @click="slideTo(index)"
            >
              {{ item.tagName }}
            </div>
          </div>
        </div>
      </div>

      <div
        class="slider-wrapper"
        data-aos="fade"
      >
        <swiper
          class="concept-swiper"
          :effect="'creative'"
          :creativeEffect="
            isMobile
              ? {
                  prev: {
                    translate: ['-20%', 0, -200], // 只露出 20%，其餘 80% 壓在後面
                  },
                  next: {
                    translate: ['20%', 0, -200],
                  }
                }
              : {
                  prev: {
                    translate: ['-80%', 0, -500], // 電腦版維持原樣
                  },
                  next: {
                    translate: ['80%', 0, -500],
                  }
                }
          "
          :grabCursor="true"
          :slidesPerView="'auto'"
          :centeredSlides="true"
          :loop="true"
          :speed="1000"
          :autoplay="{
            delay: 5000,
            disableOnInteraction: false
          }"
          :modules="modules"
          @swiper="onSwiper"
          @slideChange="onSlideChange"
        >
          <swiper-slide
            v-for="(item, index) in conceptData"
            :key="index"
            class="concept-slide"
          >
            <div class="img-box">
              <img
                :src="item.img"
                :alt="item.tagName"
              />
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

<style lang="scss" scoped>
@import '@/assets/style/function.scss';

.s5 {
  width: 100%;
  background-color: #fff;
  position: relative;
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;

  @media screen and (min-width: 768px) {
    background-image: url(./s5/bg.jpg);
  }

  .container {
    padding: sizem(30) 0;

    @media screen and (min-width: 768px) {
      max-width: 1300px;
      margin: 0 auto;
      padding: size(50) size(30);
    }

    .title {
      text-align: center;
      margin-bottom: sizem(30);

      @media screen and (min-width: 768px) {
        text-align: left;
        margin-bottom: size(40);
      }

      h2 {
        color: #00ba00;
        font-weight: 400;
        font-size: sizem(14.23);
        line-height: 1;
        position: relative;
        padding-bottom: sizem(50);

        
        @media screen and (min-width: 768px) {
          padding-bottom: size(120);
          font-size: size(33);
          line-height: 1.3;
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
            bottom: size(10);
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
          grid-template-columns: repeat(4, 1fr);
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

    .slider-wrapper {
      padding: 0 sizem(30);
      transform: scale(0.9);
      @media screen and (min-width: 768px) {
        transform: unset;
        padding: 0;
      }

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
          border-radius: sizem(5);
          overflow: hidden;
          box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);

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
    background: linear-gradient(145deg, #52D300 14.09%, rgba(80, 205, 0, 0) 85.88%); // 延用前組漸層設定
    animation: floating 4.8s ease-in-out infinite;

    @media (max-width: 768px) {
      width: size-m(67.95);
      height: size-m(67.93);
      top: size-m(220.34);
      left: size-m(269.11);
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
    background: linear-gradient(322.79deg, #52D300 14.25%, rgba(80, 205, 0, 0) 85.62%);
    animation: floating 6.2s ease-in-out infinite;

    @media (max-width: 768px) {
      width: size-m(80.7);
      height: size-m(80.68);
      top: size-m(310.85);
      left: size-m(27.61);
    }
  }

  // 第三顆球 (電腦版隱藏)
  &3 {
    display: none;

    @media (max-width: 768px) {
      display: block;
      position: absolute;
      width: size-m(32.17);
      height: size-m(32.16);
      top: size-m(120.35);
      left: size-m(93.93);
      opacity: 1;
      background: linear-gradient(109.22deg, #52D300 10.73%, rgba(80, 205, 0, 0) 89.26%);
      animation: floating 5.2s ease-in-out infinite;
    }
  }
}

@keyframes floating {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-18px);
  }
}
}
</style>
