<template>
  <div class='home-view' :class="{'light-on':state.switch,'enter-move-home':state.switch,'light-off':!state.switch}">
    <LightView @switch-active="switchActive" :switch-state="state.switch"></LightView>
  </div>
</template>
<script setup>
import LightView from '@/components/home/light-view.vue'
import '@/theme/components/light.css'
import { reactive } from 'vue';
const state = reactive({
  switch: false
})

function switchActive() {
  state.switch = !state.switch
}
</script>
<style lang='scss'>
.home-view {
  position: relative;
  width: 100vw;
  height: 100vh;
  transition: all 1s;
  background-color: var(--light-background);
}

.enter-move-home {
  animation-name: home-move;
  animation-delay: 2s;
  animation-duration: 3s;
  animation-iteration-count: 1;
  animation-fill-mode: forwards;

  @keyframes home-move {
    50% {
      // background-color: var(--light-background);
    }

    100% {
      background-color: #ffffff;
    }
  }
}
</style>
