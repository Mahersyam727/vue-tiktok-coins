<script>
import AppStep1 from './AppStep1.vue';
import AppStep2 from './AppStep2.vue';
import AppStep3 from './AppStep3.vue';

import { getRandomInteger } from '../utils/random';
export default {
  components: { AppStep1, AppStep2, AppStep3 },
  props: {
    step: {
      type: Number,
      required: true,
    },
    price: {
      type: Number,
      required: true,
    },
  },
  emits: {
    next: null,
    close: null,
  },
  methods: {
    handleBackdropClick() {
      if (this.step === 3) this.$emit('close');
    },
  },
  watch: {
    step(v) {
      if (v === 2) {
        setTimeout(() => {
          this.$emit('next');
        }, getRandomInteger(4000, 7000));
      }
    },
  },
};
</script>

<template>
  <div class="backdrop" @click="handleBackdropClick">
    <transition name="fade">
      <app-step1 v-if="step === 1" />
    </transition>
    <transition name="fade">
      <app-step2 v-if="step === 2" :price="price" />
    </transition>
    <transition name="fade">
      <app-step3 v-if="step === 3" :price="price" />
    </transition>
  </div>
</template>

<style lang="scss">
.backdrop {
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-family: ProximaNova;
  }
  position: fixed;
  z-index: 99999;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(#000, 0.3);
  // background: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
}
.container {
  @media screen and (min-width: 425px) and (max-width: 1160px) {
    width: calc(100% - 144px);
    min-width: 400px;
  }
  @media screen and (min-width: 1160px) {
    max-width: 1140px;
  }
  width: calc(100% - 2rem);
  margin: 0 auto;
  padding: 2rem;
  border-radius: 0.5rem;
  background: #fff;
  position: absolute;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
