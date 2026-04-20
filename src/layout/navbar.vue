<template>
  <div
    class="nav fixed z-[100]"
    :class="{ 'r16-9': higherScreen }"
  >
    <div
      class="menu-btn cursor-pointer flex items-center justify-center"
      @click="menuOpen = true"
      v-if="!menuOpen"
    >
      <div class="bar"></div>
    </div>

    <div
      class="menu flex flex-col items-center justify-center"
      :class="{ open: menuOpen }"
    >
      <div
        class="close-btn"
        @click="menuOpen = false"
      >
        <div class="close-icon"></div>
      </div>

      <nav class="menu-list">
        <template
          v-for="(item, i) in info.navList"
          :key="i"
        >
          <div
            class="menu-item cursor-pointer"
            @click="
              scrollTo(
                item.target,
                $isMobile() ? item.offsetmo || 0 : item.offset || 0
              )
            "
          >
            <span class="main-char">{{ item.name.charAt(0) }}</span>
            <span class="sub-text">{{ item.name.substring(1) }}</span>
          </div>
        </template>
      </nav>

      <div class="reserve-btn-wrap">
        <button
          class="reserve-btn"
          @click="scrollTo('.s-contact')"
        >
          立即預約
        </button>
      </div>
    </div>
  </div>
  <div
    class="gotop fixed z-[98] cursor-pointer"
    :class="{ show: scrollPos > 100 }"
    @click="scrollTo('.s1')"
  ></div>
</template>

<style lang="scss">
@import '@/assets/style/function.scss';

.nav {
  position: fixed;
  top: 0;
  right: 0;
  width: 100%;
  z-index: 100;

  // 漢堡按鈕樣式
  .menu-btn {
    position: absolute;
    top: size(20);
    right: size(20);
    width: size(40);
    height: size(40);

    @media screen and (max-width: 768px) {
      top: sizem(20);
      right: sizem(20);
    }

    .bar {
      width: size(35);
      height: 2px;
      background-color: #fff;
      position: relative;
      &::before,
      &::after {
        content: '';
        position: absolute;
        width: 100%;
        height: 2px;
        background-color: #fff;
        left: 0;
      }
      &::before {
        top: -12px;
      }
      &::after {
        bottom: -12px;
      }

      @media screen and (max-width: 768px) {
        width: sizem(30);
        &::before {
          top: -6px;
        }
        &::after {
          bottom: -6px;
        }
      }
    }
  }

  .menu {
    position: fixed;
    top: 0;
    right: 0;
    height: 100vh;
    background-color: #33852d; // 截圖綠色
    transition: transform 0.5s ease;
    transform: translateX(100%);
    padding: size(60) 0;

    // 寬度限制
    width: size(375);
    @media screen and (max-width: 768px) {
      width: 100%;
      padding: sizem(60) 0;
    }

    &.open {
      transform: translateX(0);
    }

    // 關閉按鈕
    .close-btn {
      position: absolute;
      top: size(30);
      right: size(30);
      width: size(40);
      height: size(40);
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;

      @media screen and (max-width: 768px) {
        top: sizem(20);
        right: sizem(20);
      }

      .close-icon {
        position: relative;
        width: 100%;
        height: 100%;
        &::before,
        &::after {
          content: '';
          position: absolute;
          top: 50%;
          left: 0;
          width: 100%;
          height: 2px;
          background-color: #fff;
        }
        &::before {
          transform: rotate(45deg);
        }
        &::after {
          transform: rotate(-45deg);
        }
      }
    }

    .menu-list {
      display: flex;
      flex-direction: column;
      gap: size(25);
      margin-bottom: size(40);

      @media screen and (max-width: 768px) {
        gap: sizem(25);
        margin-bottom: sizem(40);
      }
    }

    .menu-item {
      display: flex;
      align-items: flex-end;
      color: #fff;
      line-height: 1;

      .main-char {
        font-size: size(48);
        font-weight: 500;
        margin-right: size(8);
        @media screen and (max-width: 768px) {
          font-size: sizem(48);
          margin-right: sizem(8);
        }
      }

      .sub-text {
        font-size: size(18);
        padding-bottom: size(6);
        letter-spacing: 0.1em;
        @media screen and (max-width: 768px) {
          font-size: sizem(18);
          padding-bottom: sizem(6);
        }
      }
    }

    .reserve-btn {
      background-color: #1a5319; // 深綠色
      color: #fff;
      border: none;
      border-radius: size(100);
      padding: size(12) size(60);
      font-size: size(22);
      font-weight: 500;
      letter-spacing: 0.1em;
      cursor: pointer;
      transition: background 0.3s;

      &:hover {
        background-color: darken(#1a5319, 5%);
      }

      @media screen and (max-width: 768px) {
        border-radius: sizem(100);
        padding: sizem(12) sizem(60);
        font-size: sizem(22);
      }
    }
  }
}

.gotop {
  // 保持原本 gotop 樣式，僅確保 z-index 正確
  z-index: 98;
}
</style>

<script setup>
import { inject, computed, getCurrentInstance, onMounted, ref } from 'vue';
import info from '@/info';

const menuOpen = ref(false);

const globals = getCurrentInstance().appContext.config.globalProperties;
const isMobile = computed(() => globals.$isMobile());

const higherScreen = ref(true);

const scrollPos = ref(0);

onMounted(() => {
  const ratio = window.innerHeight / window.innerWidth;

  // if (!globals.$isMobile() && ratio > 0.46875) {
  //     higherScreen.value = true
  // }

  window.addEventListener('scroll', (event) => {
    let scroll = window.pageYOffset || document.documentElement.scrollTop;
    scrollPos.value = scroll;
  });
});

const smoothScroll = inject('smoothScroll');
const scrollTo = (el, offset) => {
  const targetElement = document.querySelector(el);
  if (targetElement) {
    const numericOffset = parseInt(offset) ? parseInt(offset) : 0;
    const elementRect = targetElement.getBoundingClientRect();
    const topPosition = window.pageYOffset + elementRect.top + numericOffset;

    smoothScroll({
      scrollTo: topPosition
    });
  }
  menuOpen.value = false;
};
</script>
