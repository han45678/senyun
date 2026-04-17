<template>
  <article
    class="s2"
    id="s2"
  >
    <div class="text">
      <img
        src="./s2/title.svg"
        alt="title"
        class="title"
      />
      <img
        src="./s2/en.svg"
        alt="en"
        class="en_title pc"
      />
      <img
        src="./s2/enm.svg"
        alt="enm"
        class="en_title mb"
      />
      <h2 class="font-['Noto_Sans_TC']">
        <span>運</span>
        樞紐動能
      </h2>
      <h3 class="font-['Noto_Sans_TC']">地段潛力・科三門戶</h3>
      <p class="font-['Noto_Sans_TC']">
        以科三為名，定錨未來<br>
        以門戶之勢，串連生活<br>
        4500坪森態都芯<br>
        揭序竹科下個十年
      </p>
    </div>
  </article>
</template>

<style lang="scss" scoped>
@import '@/assets/style/function.scss';

.s2 {
  @apply relative;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: sizem(895);
  color: #00ba00;
  font-size: sizem(20);
  text-align: center;
  line-height: 1.6;
  letter-spacing: 0.1em;
  background-image: url(./s2/bgm.jpg);
  background-size: 100% auto;
  background-position: 50% 50%;
  position: relative;
  @media screen and (min-width: 768px) {
    height: size(1080);
    font-size: size(49);
    background-image: url(./s2/bg.jpg);
  }

  .text {
    position: absolute;
    top: sizem(55);
    left: 0;
    right: 0;
    margin: auto;
    @media screen and (min-width: 768px) {
    top: size(70);
    }
    .title {
      display: block;
      width: sizem(245);
      @media screen and (min-width: 768px) {
        width: size(795);
      }
    }

    .en_title {
      width: sizem(250);
      margin-top: sizem(50);

      &.pc {
        display: none;
      }
      &.mb {
        display: block;
      }

      @media screen and (min-width: 768px) {
        width: size(970);
        margin-top: size(50);
        &.pc {
          display: block;
        }
        &.mb {
          display: none;
        }
      }
    }

    h2 {
      font-weight: 400;
      font-size: sizem(14.23);
      line-height: 1.2;
      margin-top: sizem(120);
      @media screen and (min-width: 768px) {
        font-size: size(33);
        line-height: 1.3;
        text-align: center;
        margin-top: 0;
      }

      span {
        font-weight: 400;
        font-size: sizem(52.71);
        line-height: 1.2;
        letter-spacing: 0%;
        display: block;
        @media screen and (min-width: 768px) {
          font-size: size(125);
          line-height: 1.3;
        }
      }
    }
    h3 {
      font-weight: 700;
      font-size: sizem(14);
      line-height: 1.2;
      writing-mode: vertical-lr;
      margin-left: auto;
      margin-right: auto;
      margin-top: sizem(40);
      margin-bottom: sizem(40);
      @media screen and (min-width: 768px) {
        writing-mode: unset;
        font-size: size(33);
        text-align: center;
        margin-top: size(30);
        margin-bottom: 0;
      }
    }
    p {
      font-weight: 400;
      font-size: sizem(12);
      line-height: 1.5;
      letter-spacing: 0%;
      text-align: center;
      color: #666666;
      @media screen and (min-width: 768px) {
        font-weight: 400;
        font-size: size(26);
        line-height: 1.7;
      }
    }
  }
}
</style>
<script setup></script>
