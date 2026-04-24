<template>
  <div class="contact-info-img relative">
  </div>
  <div class="contact-bg">
    <div class="contact-info mx-auto  flex flex-col items-center justify-between">
      <!--  <div class="logo">
      <img src="@/section/s1/logo.svg" alt="" data-aos="zoom-out" data-aos-delay="300" data-aos-duration="1000"/>
    </div> 
    <img src="@/section/s1/logo.svg" class="logo" alt=""> -->

      <div class="flex justify-between w-full contact-item-box">
        <div class="flex contact-item justify-center items-center" @click="modalOpen = true; modalType = 'phone'"
          v-if="info.phone">
          <img src="//h35.banner.tw/img/form/phone.svg" alt="電話" srcset="" />
          <div>{{ info.phone }}</div>
        </div>
        <div class="flex contact-item justify-center items-center" @click="modalOpen = true; modalType = 'messenger'">
          <img src="//h35.banner.tw/img/form/messenger.svg" alt="Facebook 諮詢" srcset="" />
          <div>Facebook 諮詢</div>
        </div>
        <div class="flex contact-item justify-center items-center btfanpage" @click="open(info.fbLink)">
          <img src="//h35.banner.tw/img/form/fb.svg" alt="前往粉絲專頁" srcset="" />
          <div>前往粉絲專頁</div>
        </div>
             <!--
        <div class="flex contact-item justify-center items-center btfanpage" @click="open(info.line)">
          <img src="//h35.banner.tw/img/form/line.svg" alt="官方LINE" srcset="" />
          <div>官方LINE</div>
        </div>
      -->
      </div><div class="flex justify-between w-full contact-item-box no-gap" v-if="info.address">
      <div class="flex contact-item justify-center items-center address">
        <div><span v-if="info.address1">{{ info.address1 }}：</span>{{ info.address }}</div>
      </div>
      <div class="flex contact-item justify-center items-center googlemap"
        @click="modalOpen = true; modalType = 'gmap'">
        <img src="//h35.banner.tw/img/form/gmap.svg" alt="導航 GoogleMap" srcset="" />
        <div>導航 GoogleMap</div>
      </div>
    </div>
      <!--
     
      <div class="flex justify-between w-full contact-item-box no-gap" v-if="info.address">
        <div class="flex contact-item justify-center items-center address">
          <div><span v-if="info.address1">臺北辦事處：</span>台北市松山區八德路二段374號12F</div>
        </div>
        <div class="flex contact-item justify-center items-center googlemap"
          @click="modalOpen = true; modalType = 'gmap1'">
          <img src="//h35.banner.tw/img/form/gmap.svg" alt="導航 GoogleMap" srcset="" />
          <div>導航 GoogleMap</div>
        </div>
      </div>
      <div class="flex justify-between w-full contact-item-box no-gap" v-if="info.address">
        <div class="flex contact-item justify-center items-center address">
          <div><span v-if="info.address1">臺南總公司：</span>台南市南區健康路二段545號3樓</div>
        </div>
        <div class="flex contact-item justify-center items-center googlemap"
          @click="modalOpen = true; modalType = 'gmap2'">
          <img src="//h35.banner.tw/img/form/gmap.svg" alt="導航 GoogleMap" srcset="" />
          <div>導航 GoogleMap</div>
        </div>
      </div>-->

    </div>
  </div>

  <!-- Mobile contact info -->
  <div class="bg-white mo-contact-info flex justify-end w-full contact-item-box items-center">
    <!--  <img src="@/section/s1/logo.svg" class="logo" alt="雲禾月logo"  v-if="!$isMobile()"  @click="scrollTo('.s1')"> -->

    <div class="flex flex-col contact-item justify-center items-center" @click="modalOpen = true; modalType = 'phone'"
      v-if="info.phone">
      <img src="//h35.banner.tw/img/form/phone.svg" alt="撥打電話" srcset="" />
      <div>撥打電話</div>
    </div>
    <div class="flex flex-col contact-item justify-center items-center" @click="modalOpen = true; modalType = 'messenger'">
      <img src="//h35.banner.tw/img/form/messenger.svg" alt="FB 諮詢" srcset="" />
      <div>FB 諮詢</div>
    </div>
     <!--  <div class="flex flex-col contact-item justify-center items-center" @click="open(info.line)">
      <img src="//h35.banner.tw/img/form/line.svg" alt="官方LINE" srcset="" />
      <div>官方LINE</div>
    </div>
    <div class="flex flex-col contact-item justify-center items-center" @click="open()">
      <img src="//h35.banner.tw/img/form/fb.svg" alt="前往粉絲專頁" srcset="" />
      <div>粉絲專頁</div>
    </div>  -->
    <div class="flex flex-col contact-item justify-center items-center" @click="scrollTo('.order')">
      <img src="//h35.banner.tw/img/form/pen.svg" alt="預約賞屋" srcset="" />
      <div>預約賞屋</div>
    </div>
    <!--  --><div class="flex flex-col contact-item justify-center items-center"
      @click="modalOpen = true; modalType = 'gmap'"  v-if="info.address" >
      <img src="//h35.banner.tw/img/form/gmap.svg" alt="地圖導航" srcset="" />
      <div>地圖導航</div>
    </div>
  </div>

   <!-- Modal -->
  <input type="checkbox" v-model="modalOpen" id="contact-modal" class="modal-toggle" />
  <div class="modal -mt-20 md:-mt-72">
    <div class="modal-box py-12 relative flex flex-col items-center justify-center">
      <label for="contact-modal" class="btn btn-sm btn-circle absolute right-4 top-4">✕</label>
      <!-- icon -->
      <img class="h-12" v-if="modalType == 'phone'" src="//h35.banner.tw/img/form/phone.svg" alt="phone" srcset="" />
      <img class="h-12" v-else-if="modalType == 'messenger'" src="//h35.banner.tw/img/form/messenger.svg" alt="messenger" srcset="" />
      <img class="h-12" v-else-if="modalType == 'fb'" src="//h35.banner.tw/img/form/fb.svg" alt="fb" srcset="" />
      <img class="h-12" v-else-if="modalType == 'gmap'" src="//h35.banner.tw/img/form/gmap.svg" alt="gmap" srcset="" />
      <img class="h-12" v-else-if="modalType == 'line'" src="//h35.banner.tw/img/form/line.svg" alt="line" srcset="" />
      <!-- title -->
      <div class="text-xl mt-4 font-bold">{{
       modalType == 'phone' ? '賞屋專線' :
       modalType == 'messenger' ? 'Facebook Messenger' :
       modalType == 'fb' ? 'Facebook 粉絲專頁' :
       modalType == 'line' ? 'LINE賞屋客服' :
       modalType == 'gmap' ? `${info.address2?info.address2:'導航地址'}` : 
       ''
      }}</div>
      <!-- content -->
      <div class="text-md mt-4">{{ 
      modalType == 'phone' ? info.phone : 
      modalType == 'messenger' ? '線上諮詢' : 
      modalType == 'fb' ? '' :
      modalType == 'line' ? '' :
      modalType == 'gmap' ? `${info.address}` : 
      ''
      }}</div>
      <!-- btn -->
      <div class="btn btn-lg bg-color1 border-0 text-white mt-12 hover:bg-color2" @click="go()" v-if="modalType != 'phone'" v-bind:class="{
        'hidden': modalType == 'phone' && !$isMobile(),
        'btlead': modalType == 'messenger',
        'btfanpage': modalType == 'fb',
        'btsearch': modalType == 'gmap',
        'btline': modalType == 'line',
        'btcontac': modalType == 'phone'
      }">
        {{ 
        modalType == 'phone' ? '撥打電話' : 
        modalType == 'messenger' ? '立即諮詢' : 
        modalType == 'fb' ? '前往粉絲專頁' :
        modalType == 'line' ? '加入' :
        modalType == 'gmap' ? '開啟導航' : 
        ''
        }}</div>
      <!-- btn phone -->
      <div class="btn btn-lg bg-color1 border-0 text-white mt-12 hover:bg-color2" @click="go()" id="phonegtm" v-else v-bind:class="{
        'hidden': modalType == 'phone' && !$isMobile(),
        'btlead': modalType == 'messenger',
        'btfanpage': modalType == 'fb',
        'btsearch': modalType == 'gmap',
        'btline': modalType == 'line',
        'btcontac': modalType == 'phone'
      }">
        {{ modalType == 'phone' ? '撥打電話' : modalType == 'messenger' ? '立即諮詢' : modalType == 'fb' ? '前往粉絲專頁' :
        '開啟導航'
        }}</div>
    </div>
  </div>


</template>

<style lang="scss">
@import "@/assets/style/function.scss";

.bg-color1 {
  background-color: #006a00;
}

.hover\:bg-color2:hover {
  background-color: #00a89a;
}

.mo-contact-info {
  display: none;
  z-index: 99;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: size(60);
  background: linear-gradient(90deg, #fff0 70%, #fff9);
  font-size: size(16);
  font-weight: 500;

  //backdrop-filter: blur(3px);
  .logo {
    height: 90%;
    margin: 0em auto 0 1.5em;
  }

  .contact-item {
    height: 100%;
    color: #857550;
    border-left: 1px solid #fff9;
    padding: 0 .6em;
    transition: background .3s;

    img {
      margin-bottom: 0.3em;
      max-width: 1.03em;
      height: auto;
      max-height: 1.03em;
      filter: invert(50%) sepia(20%) saturate(662%) hue-rotate(4deg) brightness(88%) contrast(90%);
    }

    &:first-child {
      border-left: 0;
    }

    &:hover {
      background: #fff9;
    }
  }
}

.contact-bg {
  position: relative;
  z-index: 3;
  // background: linear-gradient(90deg, #C4A46F 14%, #E9DCA2 46%, #D1BC86 74%, #E5D69C 99%), #FFF;
}

.contact-info-img {
  position: absolute;
  height: 0;width: 100%;
  z-index: 1;

  .f1 {
    position: absolute;
    width: size(405);
    top: size(-386);
    left: size(-144);
  }

  .f2 {
    position: absolute;
    width: size(339);
    top: size(-221);
    left: size(164);
  }

  .f3 {
    position: absolute;
    width: size(376);
    top: size(-137);
    left: size(384);
  }

  .f4 {
    position: absolute;
    width: size(488);
    top: size(-204);
    right: size(107);
  }

  .f5 {
    position: absolute;
    width: size(465);
    top: size(-312);
    right: size(-169);
  }

}

.contact-info {
  padding: size(55) size(0) size(55) size(0);
  width: size(1440);
  margin-top: size(60);
  min-width: 680px;
  position: relative;
  z-index: 50;
  // background: #045147;

  .logo {
    position: relative;
    width: size(540);
    // height: size(172);
    // background-image: url("@/section/s1/logo.svg");
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
    margin: size(60) auto size(30);
  }

  .contact-item-box {
    position: relative;
    margin-top: size(20);
    gap: size(20);
    width: size(1200);
    min-width: 750px;
    // min-width: 680px;

    .contact-item {
      background:#fff;
      color: #00744a;
      width: 100%;
      flex: 1;
      padding: 1.1em 0;
       border-radius: .9em;
      font-size: 16px;
      font-weight: 700;
      line-height: 1.6; //3.8
      letter-spacing: 0em;
      // max-width: size(280);
      z-index: 1;
      transition: all .3s;
      cursor: pointer;
      border: 1px solid #0c0;

      gap: 1em;

      &:hover {
        background: #196B19;
        color: #fff;

        img {
          filter: brightness(0) invert(1);
        }
      }

      img {
        max-width: size(27);
        height: auto;
        max-height: size(27);
        filter: invert(31%) sepia(12%) saturate(4096%) hue-rotate(76deg) brightness(95%) contrast(89%);
        transition: all .5s;
        margin: 0;
      }

      &.address {
        background-color: #ddd;
        background-image: none;
        color: #000;
        z-index: 0;
        position: relative;
        flex: 2.17;
        border: 0;
        //  max-width: 9999px;
        justify-content: center;
        margin: 0 -3.8em 0 0;

        &::before {
          content: "";
          position: absolute;
          width: 8em;
          height: 100%;
          background-color: transparent;
          left: calc(100% - 4em);
          z-index: -1;
        }

        div {
          text-indent: 0em;
          white-space: normal;
          padding: 0 1em;
        }
      }


      &.googlemap {
        flex: 1;
        //    background-color: #9B1E44;
       // border-left-width: 0;
        //  color: #fff;
        /*
        img {
          filter: brightness(0) invert(0);
        }

        &:hover {
   //     background-color: #C29267;
          color: #000;
          img {
            filter: brightness(0) invert(0);
          }
        }
          */
      }
    }

    &.no-gap {
      gap: 0 !important;
    }
  }
}

.modal-box {
  img {
    filter:  invert(30%) sepia(26%) saturate(2642%) hue-rotate(123deg) brightness(98%) contrast(101%);
  }
}

@media screen and (max-width:768px) {


  .mo-contact-info {
    display: flex;
    top: auto;
    bottom: 0;
    width: sizem(375);
    height: sizem(63);
    gap: sizem(1);
    box-shadow: 0 0 sizem(50) rgba(0, 0, 0, 0.501);
    font-size: sizem(16);
background: linear-gradient(0deg, #00a89a 0%, #006a00 100%), #04836E;

    .contact-item {
      flex: 1;
      padding: 0;
      color: #fff;

      img {
        filter: brightness(0) invert(1);
      }
    }
  }

  .contact-info {
    width: 100%;
    min-width: 0;
    padding: sizem(40) 0 sizem(40) 0;
    margin-top: sizem(60);
    position: relative;
    justify-content: space-between;
    background-size: sizem(450) auto;

    .logo {
      width: sizem(290);
      margin: sizem(40) auto sizem(30) auto;
    }

    .contact-item-box {
      position: relative;
      margin-top: sizem(0);
      gap: sizem(15);
      flex-direction: column;
      width: sizem(310);
      min-width: 0;

      .contact-item {
        padding: 1.1em sizem(80);
        font-size: sizem(16);
        max-width: 100%;
        white-space: nowrap;
        margin: 0;

        img {
          max-width: sizem(27);
          height: auto;
          max-height: sizem(27);
          margin: unset;
          position: absolute;
          left: calc(50% - 5em);
          transform: translateX(-50%);
        }

        div {
          text-indent: 2em;
        }

        &.address {
          font-size: sizem(15);
           border-radius: .9em  .9em 0 0;
          padding: 1.1em 0;
          margin: sizem(25) auto 0;
          //font-size: .9em;

          &::before {
            width: 100%;
            height: 100%;
            bottom: -50%;
            left: 0;
          }
        }

        &.address+div {
            border-radius: 0 0 .9em .9em;
        }

        &.googlemap {
        /*  border-top-width: 0;
          border-left-width: 1px; */
        }
      }

      &.no-gap {
        gap: 0 !important;
      }
    }
  }
}
</style>

<script setup>
import info from "@/info"
import { inject, ref } from "vue";
const modalOpen = ref(false);
const modalType = ref('');

const go = () => {
  if (modalType.value == 'phone') {
    window.location.href = `tel:${info.phone.replace("-", "")}`;
    setTimeout(() => {
      window.location.href = "phoneThanks";
    }, 1000);
  } else if (modalType.value == 'messenger') {
    window.open(info.fbMessage);
  } else if (modalType.value == 'gmap') {
    window.open(info.googleLink);
  }
}

const open = (link) => {
  window.open(link);
}


const smoothScroll = inject('smoothScroll')
const scrollTo = (el) => {
  smoothScroll({
    scrollTo: document.querySelector(el)
  })
}

</script>