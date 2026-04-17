<template>
  <article
    class="s1"
    id="s1"
  >
    <video
      class="bg-video"
      src="https://www.w3schools.com/html/mov_bbb.mp4"
      autoplay
      loop
      muted
      playsinline
    ></video>
    <img
      src="./s1/slogo.svg"
      class="slogo"
      alt="logo"
      data-aos="zoom-in"
      data-aos-delay="500"
    />
    <img
      src="./s1/logo.svg"
      class="logo"
      alt="logo"
      data-aos="zoom-in"
      data-aos-delay="500"
    />
  </article>
</template>

<style lang="scss" scoped>
@import '@/assets/style/function.scss';

@keyframes an {
  to {
    transform: translateX(0%);
  }
}

.s1 {
  @apply relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: calc(100dvh - #{sizem(63)});
  min-height: sizem(604);
  max-height: sizem(750);
  color: #fff;
  font-size: sizem(14);

  @media screen and (min-width: 768px) {
    height: 100dvh;
    min-height: size(900);
    max-height: size(1080);
    font-size: size(35);
  }

  .bg-video {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    z-index: 1;
    pointer-events: none;
  }

  .t0 {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    opacity: 0.3;
    pointer-events: none;
    user-select: none;
    z-index: 99;
  }
  .slogo {
    width: sizem(130);
    position: absolute;
    top: sizem(225);
    top: calc(50% + #{sizem(225 - 604 * 0.5)});
    left: 0;
    right: 0;
    margin: auto;
    z-index: 2;

    @media screen and (min-width: 768px) {
      width: size(340);
      top: size(350);
      top: calc(50% + #{size(350 - 1080 * 0.5)});
    }
  }

  .logo {
    width: sizem(200);
    position: absolute;
    top: sizem(260);
    top: calc(50% + #{sizem(260 - 604 * 0.5)});
    left: 0;
    right: 0;
    margin: auto;
    z-index: 2;

    @media screen and (min-width: 768px) {
      width: size(490);
      top: size(440);
      top: calc(50% + #{size(440 - 1080 * 0.5)});
    }
  }
  /*
  .bg {
    width: 100%;
    height: 100%;
    object-fit: cover;
    position: absolute;
    top: 50%;left: 0;transform: translateY(-50%);
    z-index: 1;
    img{
      width: 100%;
    height: 100%;
      object-fit: cover;
    transform-origin: 50% 29%;
  @media screen and (min-width: 768px) {
    height: auto;
    }
    }

  @media screen and (min-width: 768px) {
    height: auto;
    }
  }
  .cover {
    position: absolute;
    top: 50%;left: 0;right: 0;margin: auto;
    width: 100%;height: 100%;
    background: linear-gradient(0deg,#089EFB00,#089EFB 50%,#089EFBcc 70%,#089EFB00);
   z-index: 1;
    pointer-events: none;user-select:none;
    @media screen and (min-width: 768px) {
    top: 20%;height: 160%;
    }
  }
    */
}
</style>
<script setup>
import { computed, getCurrentInstance, ref, inject } from 'vue';
const globals = getCurrentInstance().appContext.config.globalProperties;

const isMobile = computed(() => globals.$isMobile());

const smoothScroll = inject('smoothScroll');
const scrollTo = (el) => {
  smoothScroll({
    scrollTo: document.querySelector(el)
  });
};
</script>
