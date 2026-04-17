<template>
  <article class="s3" id="s3">
    <div class="t1" data-aos="fade-up" data-aos-delay="0">自然之森&ensp;明日之藴</div>
    <div class="t2" data-aos="fade-up" data-aos-delay="200"><span><span class="i">4,500</span><span class="s">坪</span>森態都芯</span>
      定義未來，就從回歸初心開始</div>
    <div class="c">空拍示意圖 實際環境依現況為主
    </div>
<svg class="water" viewBox="0 5 1920 460">
  <defs>
    <filter id="water">
      <feTurbulence type="turbulence" baseFrequency="0.02"
        numOctaves="3" result="turb">
        <animate attributeName="baseFrequency"
          values="0.018; 0.020; 0.018"
          dur="20s" repeatCount="indefinite"/>
      </feTurbulence>
      <feDisplacementMap in="SourceGraphic" in2="turb"
        scale="12" xChannelSelector="R" yChannelSelector="G"/>
    </filter>
  </defs>
        <image href="./s3/bg2w.jpg"
    width="100%" height="100%"
    filter="url(#water)"/>
        
      </svg>
  <img src="./s3/bg2.png" class="water">
  </article>
</template>

<style lang="scss" scoped>
@import '@/assets/style/function.scss';

@keyframes an {
  to {
    transform: translateX(0%);
  }
}

.s3 {
  @apply relative;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  height:sizem(615);
  // background: #d62051;
  background: #089EFB url("./s3/bgm.jpg") no-repeat;
  background-size: 100% auto;
  background-position: 50% 100%;
  color: #FFF;
  font-size: sizem(14);
  // text-align: center;
  line-height: 1.6;
  letter-spacing: .1em;

  @media screen and (min-width: 768px) {
    background-image: url("./s3/bg.jpg");
    background-size: cover;
    background-position: 50% 100%;
    height: size(1335);
    font-size: size(34);
    justify-content: flex-start;
    margin-bottom: size(-250);
   // padding: 0 0 0 size(850);
  }


  .t1 {
    font-size: sizem(32);
    line-height: 1.3;
    font-weight: 500;
    position: relative;
    z-index: 3;
    margin: 2.7em auto .2em;
    letter-spacing: .10em;

    @media screen and (min-width: 768px) {
      font-size: size(105);
    margin: 1.2em auto .25em;
    letter-spacing: .14em;
    }
  }

  .t2 {
   font-size: sizem(12);
    font-weight: 400;
    margin-bottom: .6em;
    position: relative;
    letter-spacing: 0.06em;
    z-index: 3;
    color: #0008;
    text-align: center;
    line-height: 1.35;
    > span{display: block;
    font-size: 1.9em;
    letter-spacing: 0.05em;
    text-indent: 0.05em;
    }
    .i{
    letter-spacing: 0em;
    }
    .s{
      font-size: 0.45em;margin-right: 0.2em;
    }

    @media screen and (min-width: 768px) {
      font-size: size(40);
    }
  }

  .c {
    position: absolute;
    bottom: 0.5em;
    left: 0.5em;
    letter-spacing: 0em;
    font-size: sizem(10);
    text-shadow: 1px 1px 3px #000;opacity: .6;z-index: 5;

    @media screen and (min-width: 768px) {
      font-size: size(13);
    bottom: 20.5em;
    }
  }
  .water{bottom:0;position: absolute;width: 100%;left: 0;opacity: 1;}

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