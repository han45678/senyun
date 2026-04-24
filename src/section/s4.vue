<template>
  <article class="s4" id="s4">
    <Fullview />
  </article>
</template>

<style lang="scss" scoped>
@import '@/assets/style/function.scss';

.s4 {
  @apply relative;

  //height: size(1080);
  //height: 100dvh;
  @media screen and (max-width: 767px) {
    height: sizem(604);
  }

  &::after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: sizem(50);
    background: linear-gradient(0deg, #01ADF900, #01ADF900, #01ADF9);

    @media screen and (min-width: 768px) {
      height: size(70);
    }
  }
}
</style>
<script setup>
import Fullview from '@/components/fullview.vue';
</script>
