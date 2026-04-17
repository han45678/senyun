<template>
  <article class="s2" id="s2">
    <div class="t1" data-aos="fade-up" data-aos-delay="0">科三門戶特區</div>
 
    <div class="t2" data-aos="fade-up" data-aos-delay="400"><img src="./s1/slogo.svg" class="slogo" alt="slogo" /><br v-if="isMobile"><span>年度鉅獻</span></div>
 
 <div class="line"></div>
    <div class="t3" data-aos="fade-up" data-aos-delay="400">限量早鳥預約起跑<br v-if="isMobile">
快馬搶先</div>
    <div class="t4" data-aos="fade-up" data-aos-delay="400">即將公開
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 74 37">
  <defs>
    <linearGradient id="lg" x1="0" y1="0" x2="0" y2="37"  gradientUnits="userSpaceOnUse">
      <stop offset="0" stop-color="#d6f1ff00"/>
      <stop offset="1" stop-color="#c2e5ff"/>
    </linearGradient>
  </defs>
    <path d="M73.7,0l-36.8,36.8L0,0" fill="url(#lg)"/>
</svg></div>
<img src="./s2/en.svg" class="en" alt="en" />

  </article>
</template>

<style lang="scss" scoped>
@import '@/assets/style/function.scss';

@keyframes an {
  to {
    transform: translateX(0%);
  }
}

.s2 {
  @apply relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height:sizem(604);
  background: linear-gradient(180deg, #0085E5 0%, #19B2FF 50%, #67D2FF 100%);
  // background: #d62051;
 /* background: #089EFB url("./s2/bgm.jpg") no-repeat;
  background-size: 100% auto;
  background-position: 50% 100%;*/
  color: #FFF;
  font-size: sizem(20);
  text-align: center;
  line-height: 1.6;
  letter-spacing: .1em;

  @media screen and (min-width: 768px) {
   /* background-image: url("./s2/bg.jpg");
    background-size: cover;
    background-position: 50% 50%;
    */
    height: 100dvh;
    min-height: size(900);
    max-height: size(1080);
    font-size: size(49);
   // justify-content: flex-end;
  }


  .t1 {
    font-size: sizem(38);
    line-height: 1.2;
    font-weight: 500;
      position: relative;
      z-index: 3;
      letter-spacing: .1em;
      margin-bottom: 1.2em;

    @media screen and (min-width: 768px) {
      font-size: size(95);
      letter-spacing: .19em;
      text-indent: .19em;
      margin-bottom: .25em;
    }
  }

  .t2 {
    font-size: sizem(17);
    font-weight: 500;
      position: relative;
      z-index: 3;
img{width: sizem(130);
      margin-bottom: .8em;}
    span {
      display: inline-block;
      margin-top: 0;
      width: sizem(130);
      border: 1px solid currentColor;
      letter-spacing: .5em;text-indent: .5em;
    }

    @media screen and (min-width: 768px) {
      font-size: size(35);
      margin-bottom: 0em;
img{width: size(350);
      margin-bottom: .8em;margin-right: 1em;}

    span {
      width: size(268);vertical-align: .3em;
    }
    }
  }

  .line {
      position: relative;
    width: 1px;
    height: 5.5em;
    background: currentColor;
    margin: 1.4em 0em 1.4em 0em;
      z-index: 3;

    @media screen and (min-width: 768px) {
    width: 13.5em;
    height: 1px;
    margin: .8em 0em 1.4em 0em;
     // display: none;
    }

  }

  .t3 {
    margin-bottom:2.3em;
      position: relative;
      z-index: 3;
      line-height: 1.2;

    @media screen and (min-width: 768px) {
      margin-bottom: 0em;
      letter-spacing: 0.1em;
    }
  }

  .t4 {
      position: relative;
    margin-bottom:1.7em;
      z-index: 3;
      font-weight: 300;
      svg{width: 1.6em;margin:.3em auto auto;}

    @media screen and (min-width: 768px) {
      margin-bottom: 1.7em;
      letter-spacing: 0.1em;
    font-size: size(57);
      svg{width: 1.2em;margin:.4em auto auto;}
    }
  }

  .en {
    width: sizem(368);
    position: absolute;
    bottom: sizem(7);
    left: 0;right: 0;margin: auto; z-index: 2;

    @media screen and (min-width: 768px) {
      width: size(1880);
      bottom: size(10);
    }
  }

}
</style>
<script setup>
import { computed, getCurrentInstance, ref, inject } from 'vue';
const globals = getCurrentInstance().appContext.config.globalProperties;

const isMobile = computed(() => globals.$isMobile());

const smoothScroll = inject('smoothScroll')
const scrollTo = (el) => {
  smoothScroll({
    scrollTo: document.querySelector(el)
  })
}
</script>