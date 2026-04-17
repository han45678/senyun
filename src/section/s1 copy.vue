<template>
  <article class="s1" id="s1">
   <!-- <img src="./s1/mo.jpg" class="t0">
    <img src="./s1/mo.jpg" class="t0">  -->
      <img src="./s1/logo.svg" class="logo" data-aos="zoom-in" data-aos-delay="0">

      <img src="./s1/t1m.svg" class="t1" data-aos="zoom-in" data-aos-delay="0" v-if="isMobile">
      <img src="./s1/t1.svg" class="t1" data-aos="zoom-in" data-aos-delay="0" v-else>

      <img src="./s1/bird.webp" class="bird" data-aos="fade-up" data-aos-delay="400">

   <!--  <img src="./s1/s1bg.jpg" class="bg" v-else> 
    <div class="txt">
      <h2 class="t1" data-aos="zoom-in" data-aos-delay="0">在這裡<br>發現布魯克林</h2>
      <div class="t2" data-aos="zoom-in" data-aos-delay="200">紐約曼哈頓，為布魯克林而美麗<br>
台灣的布魯克林，驚喜發現在八里<br>
同步匯集智慧、綠意、人文城市於一身</div>
<div class="t3" data-aos="zoom-in" data-aos-delay="400">國際心跳 矚目之光<span>蓄勢待發</span></div>
<img src="./s1/en.svg" class="en" data-aos="zoom-in" data-aos-delay="600"> 
    </div>
  -->
  </article>
</template>

<style lang="scss" scoped>
@import '@/assets/style/function.scss';

@keyframes op {
  50% {
     opacity: 0;
  }
}
@keyframes an {
  to {
    transform: translateX(0%);
  }
}
.s1 {
  @apply relative; 
  display: flex;
  flex-direction: column;
  justify-content:center;
  align-items:center;
  height:sizem(605);
  //background: #d62051;
  background: url("./s1/bgm.webp");
  background-size:cover ;
  @media screen and (min-width: 768px) {
    background: url("./s1/bg.webp");
    background-size:cover ;
    height:100vh;
    max-height:size(1080);
    min-height:size(900);
  }
  //background: #E60012;
// padding-bottom: size(140);V
 // &::after{content: "";position: absolute;bottom: 0;height: 1px;width: size(1552);left: 0;right: 0;margin: auto;background: #0006;}

.t1{width:sizem(250);
    position: absolute;
    z-index: 99;
    top:sizem(30);
    right: sizem(60);
}
.logo{
width:sizem(250);
top:sizem(70);
position: absolute;
z-index: 99;
}
.bird{
position: absolute;
width:sizem(280);
bottom:0;
left: auto;
right: sizem(40);
top: auto;
margin: 0;
}

@media screen and (min-width: 768px) {


.t1{
  position: absolute;
  right: size(60);
  top:size(60);
  width:size(250);}

.logo{
width:size(631);
top:size(180);
left: size(280);

}
.bird{
  position: absolute;
  width:auto;
  height: 100vh;
  top:size(0);
  right: size(100);
  left:auto;
  bottom: 0;
  rotate: 0deg;
}
}

}

  
/* 螢幕尺寸標準 */
/* 平板尺寸 */
/*
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) {}

@media screen and (max-width: 767px) {
  .s1 {
    font-size:sizem(14);
    .txt{
    top: sizem(85);
    .en{width: 18em;}
  }
}
}
*/
</style>
<script setup>
import { computed, getCurrentInstance, ref ,inject} from 'vue';
const globals = getCurrentInstance().appContext.config.globalProperties;

const isMobile = computed(() => globals.$isMobile());

const smoothScroll = inject('smoothScroll')
const scrollTo = (el) => {
  smoothScroll({
    scrollTo: document.querySelector(el)
  })
}
</script>