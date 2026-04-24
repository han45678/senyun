<template>
  <section class="s7">
    <div class="top">
      <div class="text font-['Noto_Sans_TC']">
        <h2
          data-aos="fade-up"
          data-aos-delay="0"
        >
          <span>藴</span>
          未來之境
        </h2>
        <h3
          data-aos="fade-up"
          data-aos-delay="200"
        >
          公設美學・全齡宜居
        </h3>
        <p
          data-aos="fade-up"
          data-aos-delay="500"
        >
          每個階段，都有家陪伴，孩子的笑，青年的夢<br />公設裡世代共融，翻開書頁，找到心的歸屬
        </p>
      </div>
      <img
        class="en_title"
        src="./s7/en_title.svg"
        alt="en_title"
          data-aos="fade-up"
        data-aos-delay="400"
      />

      <p class="txt font-['Noto_Sans_TC']">以上圖片為AI情境模擬。</p>
    </div>
    <div class="marquee-wrapper">
      <div class="marquee-content">
        <div
          v-for="i in 2"
          :key="i"
          class="marquee-group"
        >
          <div
            v-for="(item, index) in marqueeData"
            :key="`${i}-${index}`"
            class="marquee-item"
            @click="openModal(item)"
          >
            <div class="img-box">
              <img
                :src="item.thumb"
                :alt="item.name"
              />
            </div>
            <div class="info">
              <p class="name font-['Noto_Sans_TC']">{{ item.name }}</p>
              <p class="area font-['Noto_Sans_TC']" v-html="item.area"></p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <Transition name="fade">
      <div
        v-if="isModalOpen"
        class="modal-mask"
        @click.self="closeModal"
      >
        <div class="modal-container">
          <button
            class="close-btn"
            @click="closeModal"
          >
            <img
              src="./s7/close.svg"
              alt="close"
            />
          </button>

          <div
            class="modal-content"
            v-if="selectedItem"
          >
            <div class="img-box">
              <img
                :src="selectedItem.bigImg"
                :alt="selectedItem.name"
              />
            </div>
            <div class="text-box">
              <h3>{{ selectedItem.name }}</h3>
              <p class="desc" v-html="selectedItem.area"></p>
            </div>
          </div>
        </div>
      </div>
    </Transition>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const isModalOpen = ref(false);
const selectedItem = ref(null);

const marqueeData = [
  {
    name: '紀伊國屋書店選冊',
    area: '以上圖片為AI情境模擬<br>　',
    thumb: new URL('./s7/1.jpg', import.meta.url).href,
    bigImg: new URL('./s7/b1.jpg', import.meta.url).href
  },
  {
    name: 'Novus Nest遊戲區',
    area: '遊戲區3D情境示意圖(包含外觀建材、設施、植栽、地坪鋪面、周邊環境等)僅供參考。賣方於不違反廣告真實性條件下，保有調整與修改權。另因印刷色澤與完工實品會略有差異，最終仍以實際完工及現況為準。經紀業: 昌益房屋仲介事業股份有限公司',
    thumb: new URL('./s7/2.jpg', import.meta.url).href,
    bigImg: new URL('./s7/b2.jpg', import.meta.url).href
  },
  {
    name: 'Mono Zen韻律教室',
    area: '遊戲區3D情境示意圖(包含外觀建材、設施、植栽、地坪鋪面、周邊環境等)僅供參考。賣方於不違反廣告真實性條件下，保有調整與修改權。另因印刷色澤與完工實品會略有差異，最終仍以實際完工及現況為準。經紀業: 昌益房屋仲介事業股份有限公司',
    thumb: new URL('./s7/3.jpg', import.meta.url).href,
    bigImg: new URL('./s7/b3.jpg', import.meta.url).href
  },
  {
    name: 'Workout健身中心',
    area: '遊戲區3D情境示意圖(包含外觀建材、設施、植栽、地坪鋪面、周邊環境等)僅供參考。賣方於不違反廣告真實性條件下，保有調整與修改權。另因印刷色澤與完工實品會略有差異，最終仍以實際完工及現況為準。經紀業: 昌益房屋仲介事業股份有限公司',
    thumb: new URL('./s7/4.jpg', import.meta.url).href,
    bigImg: new URL('./s7/b4.jpg', import.meta.url).href
  }
];

const openModal = (item) => {
  selectedItem.value = item;
  isModalOpen.value = true;
};

const closeModal = () => {
  isModalOpen.value = false;
};
</script>

<style lang="scss" scoped>
@import '@/assets/style/function.scss';

.s7 {
  width: 100%;
  overflow: hidden;
  background-color: #fff;
  position: relative;
 // z-index: 1;

  .top {
    height: sizem(550);
    margin-bottom: sizem(5);
    overflow: hidden;
    position: relative;
    background-image: url(./s7/bgm.jpg);
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    @media screen and (min-width: 768px) {
      height: size(760);
      background-image: url(./s7/bg.jpg);
      margin-bottom: size(10);
    }
    .text {
      text-align: center;
      margin-bottom: sizem(30);
      position: relative;
      z-index: 1;

      @media screen and (min-width: 768px) {
        text-align: right;
        padding-top: size(150);
        padding-right: size(120);
      }

      h2 {
        color: #fff;
        font-weight: 400;
        font-size: sizem(14.23);
        line-height: 1;
        position: relative;
        padding-bottom: sizem(275);
        padding-top: sizem(50);

        @media screen and (min-width: 768px) {
          padding-bottom: size(30);
          font-size: size(33);
          padding-top: 0;
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
      }

      h3 {
        color: #fff;
        font-weight: 700;
        font-size: sizem(14);
        line-height: 1.2;
        margin: sizem(15) auto;
        @media screen and (min-width: 768px) {
          font-size: size(33);
          line-height: 1.3;
          margin: size(20) 0;
        }
      }

      p {
        font-weight: 400;
        font-size: sizem(12);
        line-height: 1.7;
        color: #fff;
        @media screen and (min-width: 768px) {
          font-size: size(26);
          line-height: 1.3;
        }
      }
    }

    &::before {
      content: '';
      position: absolute;
      right: 0;
      left: 0;
      margin: auto;
      width: 100%;
      height: sizem(375);
      bottom: 0;
      background: linear-gradient(180deg, rgba(80, 205, 0, 0) 0%, #52d300 100%);

      @media screen and (min-width: 768px) {
        width: size(793);
        height: size(885);
        top: size(-62);
        left: size(1127);
        background: linear-gradient(
          90deg,
          rgba(80, 205, 0, 0) 0%,
          #52d300 100%
        );
      }
    }

    .en_title {
      position: absolute;
      z-index: 1;
      left: 0;
      right: 0;
      margin: auto;
      bottom: sizem(5);
      width: sizem(330);
      @media screen and (min-width: 768px) {
        left: size(50);
        right: unset;
        bottom: size(30);
        width: size(1000);
      }
    }

    .txt {
      position: absolute;
      right: sizem(15);
      bottom: sizem(15);
      color: #fff;
      font-weight: 400;
      line-height: 1.3;
      letter-spacing: 0%;
      text-align: right;
      vertical-align: bottom;
      font-size: sizem(12);
      display: none;
      z-index: 1;
      @media screen and (min-width: 768px) {
        right: size(15);
        bottom: size(15);
        font-size: size(12);
        display: block;
      }
    }
  }
  .marquee-wrapper {
    margin-bottom: sizem(5);
    display: flex;
    @media screen and (min-width: 768px) {
      
    margin-bottom: size(10);
    }
    .marquee-content {
      display: flex;
      animation: run 50s linear infinite;
      &:hover {
        animation-play-state: paused;
      }
    }
    .marquee-group {
      display: flex;
    }
    .marquee-item {
      cursor: pointer;
      margin-right: sizem(5);
      position: relative;
      flex: 0 0 100vw; // 手機版強制為 100% 視窗寬度

      @media screen and (min-width: 768px) {
        flex: 0 0 auto; // 電腦版恢復以內容寬度為主
        margin-right: size(10);
      }

      .img-box {
        position: relative;
        width: 100%;
        overflow: hidden;
        @media screen and (min-width: 768px) {
          width: size(601);
        }
        img {
          width: 100%;
          height: 100%;
          object-fit: cover;
        }
      }

      .info {
        position: absolute;
        left: sizem(15);
        bottom: sizem(15);
        color: #fff;
        width: calc(100% - sizem(30));

        @media screen and (min-width: 768px) {
          padding-top: size(15);
          width: calc(100% - size(30));
          left: size(15);
          bottom: size(15);
        }

        .name {
          font-weight: 400;
          font-size: sizem(18.38);
          line-height: 1.3;
          margin-bottom: sizem(5);

          @media screen and (min-width: 768px) {
            font-size: size(29.33);
            margin-bottom: size(5);
          }
        }

        .area {
          font-weight: 400;
          font-size: sizem(4.39);
          line-height: 1.3;

          @media screen and (min-width: 768px) {
            font-size: size(7);
          }
        }
      }
    }
  }
}

@keyframes run {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-50%);
  }
}

// Modal 基礎樣式
.modal-mask {
  position: fixed;
  inset: 0;
  z-index: 9999;
  display: flex;
  align-items: center;
  justify-content: center;
  // 背景與毛玻璃設定
  background: rgba(0, 0, 0, 0.6);
  backdrop-filter: blur(24px);
  -webkit-backdrop-filter: blur(24px); // 兼容 Safari
}

.modal-container {
  position: relative;
  width: 100%;
  // 手機版 100%，電腦版 1400px
  max-width: 100%;

  @media screen and (min-width: 768px) {
    max-width: size(1400);
  }

  .close-btn {
    position: absolute;
    right: sizem(5);
    bottom: calc(100% + sizem(5));
    width: sizem(40);
    height: sizem(40);
    background: none;
    border: none;
    cursor: pointer;
    z-index: 10;

    @media screen and (min-width: 768px) {
      right: size(5);
      bottom: size(75);
      bottom: calc(50% + #{size(192 - 1080 * 0.5)});
      width: size(40);
      height: size(40);
    }

    img {
      width: 100%;
      height: 100%;
    }
  }
}

.modal-content {
  width: 100%;

  .img-box {
    width: 100%;

    img {
      width: 100%;
      height: auto;
      display: block;
    }
  }

  .text-box {
    color: #fff;
    text-align: left;
    padding: 0 sizem(10);
    @media screen and (min-width: 768px) {
      padding: 0;
    }
    h3 {
      font-size: sizem(24);
      font-weight: 500;
      @media screen and (min-width: 768px) {
        font-size: size(48);
      }
    }

    .desc {
      font-size: sizem(10);
      opacity: 0.8;
      @media screen and (min-width: 768px) {
        font-size: size(16);
      }
    }
  }
}

// 動畫
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.4s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
