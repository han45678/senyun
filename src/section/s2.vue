<script setup></script>

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
        alt=""
        class="en_title pc"
      />
      <img
        src="./s2/enm.svg"
        alt=""
        class="en_title mb"
      />
      <h2 class="font-['Noto_Sans_TC']">
        <span>運</span>
        樞紐動能
      </h2>
      <h3 class="font-['Noto_Sans_TC']">地段潛力・科三門戶</h3>
      <p class="font-['Noto_Sans_TC']">
        以科三為名，定錨未來<br />
        以門戶之勢，串連生活<br />
        4500坪森態都芯<br />
        揭序竹科下個十年
      </p>
    </div>

    <div class="fs fs1" />
    <div class="fs fs2" />
    <div class="fs fs3" />
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
      position: relative;
      &::before {
        content: '';
        width: sizem(0.5);
        height: sizem(60);
        background-color: #00ba00;
        position: absolute;
        left: 0;
        right: 0;
        margin: auto;
        top: sizem(-70);
        @media screen and (min-width: 768px) {
          display: none;
        }
      }

      @media screen and (min-width: 768px) {
        font-size: size(33);
        line-height: 1.3;
        text-align: center;
        margin-top: size(50);
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

      &::before {
        content: '';
        width: sizem(0.5);
        height: sizem(60);
        background-color: #00ba00;
        position: absolute;
        left: 0;
        right: 0;
        margin: auto;
        bottom: sizem(-100);

        @media screen and (min-width: 768px) {
          width: size(0.5);
          height: size(165);
          bottom: size(-220);
        }
      }

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

  .fs {
    border-radius: 100%;
    position: absolute;

    // 第一個球體
    &1 {
      position: absolute;
      width: size(86.06);
      height: size(86.06);
      top: size(363);
      left: size(1169.1);

      background: linear-gradient(
        145deg,
        #52d300 14.09%,
        rgba(80, 205, 0, 0) 85.88%
      );
      opacity: 1;
      animation: floating 4.2s ease-in-out infinite;

      @media (max-width: 768px) {
        width: sizem(40.77);
        height: sizem(40.76);
        top: sizem(288.14);
        left: sizem(263.32);
      }
    }

    // 第二個球體
    &2 {
      position: absolute;
      width: size(137.9);
      height: size(137.9);
      top: size(491.09);
      left: size(567.01);
      background: linear-gradient(
        322.79deg,
        #52d300 14.25%,
        rgba(80, 205, 0, 0) 85.62%
      );
      opacity: 1;
      animation: floating 5.8s ease-in-out infinite;

      @media (max-width: 768px) {
        width: sizem(54.1);
        height: sizem(54.09);
        top: sizem(426.52);
        left: sizem(51.96);
      }
    }

    // 第三個球體
    &3 {
      position: absolute;
      width: size(237.02);
      height: size(237.02);
      top: size(623.09);
      left: size(1299.79);
      background: linear-gradient(
        109.22deg,
        #52d300 10.73%,
        rgba(80, 205, 0, 0) 89.26%
      );
      opacity: 1;
      animation: floating 7.5s ease-in-out infinite;

      @media (max-width: 768px) {
        width: sizem(84.66);
        height: sizem(84.64);
        top: sizem(765.14);
        left: sizem(266.14);
      }
    }
  }

  @keyframes floating {
    0%,
    100% {
      transform: translateY(0px);
    }
    50% {
      transform: translateY(-15px);
    }
  }
}
</style>
