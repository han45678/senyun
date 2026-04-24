<template>
  <article class="s8">
    <img
      class="bg pc"
      src="./s8/bg.jpg"
      alt="bg"
    />
    <img
      class="bg m"
      src="./s8/bgm.jpg"
      alt="bg"
    />

    <div class="text"  data-aos="fade-up-right"
        data-aos-delay="400">
      <h2 data-aos="fade-up"
          data-aos-delay="200">
        <span>韻</span>
        美學共生
      </h2>
      <h3 data-aos="fade-up"
          data-aos-delay="400">藝術美學・大師鉅作</h3>
      <p data-aos="fade-up"
          data-aos-delay="600">
        美在肌理與光影之間<br />
        光影落下，建築呼吸<br />
        國際藝術大師-郭國相刻劃底藴<br />
        每一道線條，都是溫柔韻腳
      </p>
    </div>

    <img class="en_title" src="./s8/en_title.svg" alt="en_title">

    <p class="txt font-['Noto_Sans_TC']">外觀3D情境示意圖(包含外觀建材、植栽、地坪鋪面、周邊環境等)僅供參考。賣方於不違反廣告真實性條件下，保有調整與修改權。另因印刷色澤與完工實品會略有差異，最終仍以實際完工及現況為準。經紀業: 昌益房屋仲介事業股份有限公司</p>

  </article>
</template>

<style lang="scss" scoped>
@import '@/assets/style/function.scss';
.s8 {
  position: relative;
  z-index: 1;
  .bg {
    width: 100%;
    &.pc {
      display: none;
      @media screen and (min-width: 768px) {
        display: block;
      }
    }
    &.m {
      display: block;
      @media screen and (min-width: 768px) {
        display: none;
      }
    }
  }

  .text {
    width: sizem(312.6);
    height: sizem(312.52);
    opacity: 1;
    top: sizem(111.64);
    left: 0;
    right: 0;
    margin: auto;
    background: linear-gradient(
      225deg,
      #52d300 14.64%,
      rgba(80, 205, 0, 0) 85.36%
    );
    border-radius: 100%;
    position: absolute;
    z-index: 1;
    text-align: center;
    @media screen and (min-width: 768px) {
      text-align: left;
      width: size(758.94);
      height: size(758.94);
      angle: 0 deg;
      opacity: 1;
      top: size(158);
      left: size(-118);
      right: unset;
      background: linear-gradient(
        227.23deg,
        #52d300 14.68%,
        rgba(80, 205, 0, 0) 85.45%
      );
      padding-top: size(150);
      padding-left: size(275);
    }

    h2 {
      color: #fff;
      font-weight: 400;
      font-size: sizem(14.23);
      line-height: 1;
      position: relative;
      padding-bottom: sizem(15);
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

  .en_title{
    position: absolute;
    top: sizem(30);
    left: 0;
    right: 0;
    margin: auto;
    width: sizem(260);
    @media screen and (min-width: 768px) {
      display: none;
    }
  }

  .txt {
      position: absolute;
      left: sizem(15);
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
        left: size(15);
        bottom: size(15);
        font-size: size(12);
        display: block;
      }
    }
}
</style>
