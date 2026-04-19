<template>
  <article class="s9">
    <img
      class="title"
      src="./s9/title.svg"
      alt="title"
    />
  </article>
</template>

<style lang="scss" scoped>
@import '@/assets/style/function.scss';
.s9 {
  position: relative;
  z-index: 1;
  background-color: #fff;
  height: sizem(375);
  display: flex;
  align-items: center;
  justify-content: center;
  @media screen and (min-width: 768px) {
    height: 100dvh;
  }
  .title {
    width: sizem(233.37);
    height: sizem(131);
    display: block;
    margin: auto;
    @media screen and (min-width: 768px) {
      width: size(1077.74);
      height: size(604.97);
    }
  }
}
</style>
