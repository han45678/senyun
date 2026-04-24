<template>
  <article
    class="s3"
    id="s3"
  >
    <img
      src="./s3/title.svg"
      alt="title"
      class="title"
      data-aos="fade-up"
      data-aos-delay="500"
    />

    <div class="bg">
      <svg
        class="water"
        viewBox="0 0 1920 1115"
      >
        <defs>
          <filter id="water">
            <feTurbulence
              type="turbulence"
              baseFrequency="0.02"
              numOctaves="3"
              result="turb"
            >
              <animate
                attributeName="baseFrequency"
                values="0.018; 0.020; 0.018"
                dur="20s"
                repeatCount="indefinite"
              />
            </feTurbulence>
            <feDisplacementMap
              in="SourceGraphic"
              in2="turb"
              scale="12"
              xChannelSelector="R"
              yChannelSelector="G"
            />
          </filter>
        </defs>
        <image
          x="-10"
          href="https://xcatx7.github.io/pics/senyun/bg.jpg"
          width="100%"
          height="100%"
          filter="url(#water)"
          transform=" scale(1.008,1.005)"
        />
      </svg>
      <img
        src="https://xcatx7.github.io/pics/senyun/gif.gif"
        class="gif"
      />
      <img
        src="https://xcatx7.github.io/pics/senyun/top.jpg"
        class="top"
      />
      <img
        src="https://xcatx7.github.io/pics/senyun/botton.png"
        class="bottom"
      />
    </div>
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
  padding-top: sizem(80);
  background-color: #3ba0ff;
  @media screen and (min-width: 768px) {
    padding-top: 0;
  }
  .title {
    position: absolute;
    left: 0;
    right: 0;
    margin: auto;
    top: sizem(30);
    width: sizem(250);
    z-index: 1;
    @media screen and (min-width: 768px) {
      width: size(570);
      top: size(200);
    }
  }
  .bg {
    position: relative;
    overflow: hidden;
    width: sizem(650);
    left:sizem(-140);
    aspect-ratio: 1920 / 1110;
    @media screen and (min-width: 768px) {
    width: 100%;
    left:0;
    }
    &::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: sizem(50);
      background:linear-gradient(180deg, #01ADF900 , #01ADF933 ,#01ADF9);
    @media screen and (min-width: 768px) {
      height: size(50);
}
    }
  }
  svg {
    width: 100%;
    aspect-ratio: 1920 / 1110;
    filter: blur(0.8px);
  }
  .top {
    position: absolute;
    width: 100%;
    top: 0;
    left: 0;
  }
  .gif {
    position: absolute;
    width: 100%;
    height: 26%;
    bottom: 2%;
    left: 0;
    mix-blend-mode: overlay;
    filter: blur(1px);
  }
  .bottom {
    position: absolute;
    width: 100%;
    bottom: 0;
    left: 0;
  }
  @media screen and (max-width: 767px) {
    svg {
      filter: blur(0.1px);
    }
    .gif {
      filter: blur(0.5px);
    }
  }
}
</style>
