<template>
  <section class="s1 relative">
    <div class="video_container">
      <iframe
        :src="videoSrc"
        frameborder="0"
        allow="autoplay; encrypted-media"
        allowfullscreen
      ></iframe>
    </div>

    <!-- 按鈕 -->
    <button class="mute_btn" @click="toggleMute">
      <svg v-if="isMuted" viewBox="0 0 24 24">
        <path
          d="M20,22l-2.5-2.5c-1,.7-2.2,1.3-3.6,1.5v-2c.8-.2,1.5-.5,2.1-.9l-4.1-4.1v6l-5-5H3v-6h4S2,4,2,4l1.6-1.6,18.1,18.1-1.6,1.6ZM14,8v2l2.1,2.1c0-1.7-.7-3.4-2.1-4.1ZM18.6,14.6l1.5,1.5c2.2-5.1.1-12.3-6.2-13.1v2c4.1,1,5.8,5.8,4.6,9.6ZM12,4l-2,2,2,2v-3.9Z"
        />
      </svg>
      <svg v-else viewBox="0 0 24 24">
        <path
          d="M14,8v8.1c2.8-1.4,2.8-6.7,0-8.1ZM3,9v6h4l5,5V4l-5,5H3ZM14,21v-2c6.9-1.5,6.4-12.5,0-14v-2c9.4,1.2,9.3,16.6,0,18Z"
        />
      </svg>
    </button>
  </section>
</template>

<script setup>
import { ref, computed, getCurrentInstance } from "vue";

const globals = getCurrentInstance().appContext.config.globalProperties;
const isMobile = computed(() => globals.$isMobile());

const isMuted = ref(true);

// 根據裝置選擇不同的影片
const videoId = computed(() =>
  isMobile.value ? "AtpOdeOJD1I" : "y8qOO-N61Yw",
);

// iframe 用
const videoSrc = computed(
  () =>
    `https://www.youtube.com/embed/${videoId.value}?autoplay=1&${
      isMuted.value ? "mute=1" : "mute=0"
    }&loop=1&playlist=${videoId.value}`,
);

const toggleMute = () => {
  isMuted.value = !isMuted.value;
};
</script>

<style lang="scss" scoped>
@import '@/assets/style/function.scss';

// 共用樣式
.s1 {
  .video_container {
    position: relative;
    width: 100%;
    margin: 0 auto;

    iframe {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
    }
  }

  .mute_btn {
    position: absolute;
    bottom: 10px;
    right: 10px;
    background: rgba(0, 0, 0, 0.6);
    border-radius: 50%;
    padding: 10px;
    z-index: 10;
    cursor: pointer;
    border: none;

    svg {
      width: 24px;
      height: 24px;
      fill: white;
      stroke: white;
    }
  }
}

// 桌機設定
@media screen and (min-width: 768px) {
  .s1 {
    .video_container {
      height: 0;
      padding-top: 56.25%; // 16:9 比例
      overflow: hidden;
      pointer-events: none;
    }
  }
}

// 手機設定
@media screen and (max-width: 767px) {
  .s1 {
    .video_container {
      aspect-ratio: 9 / 16; // 9:16 比例 (YouTube Shorts)
    }
  }
}
</style>
