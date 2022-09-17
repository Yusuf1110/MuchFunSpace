<template>
  <div class='light-view' :class="{'enter-move-light':props.switchState}">
    <div class="light-switch">
      <div class="switch-button-container">
        <div class="switch-button" :class="{'switch-button-on':props.switchState}" @click="$emit('switchActive')">
          <div class="switch-light">
          </div>
        </div>
      </div>
    </div>
    <div class="light-bulb-container">
      <div class="light-bulb-line"></div>
      <div class="light-bulb">
        <div class="light-bulb-root-bar"></div>
        <div class="light-bulb-root"></div>
        <div class="light-bulb-root"></div>
        <div class="light-bulb-root"></div>
        <div class="light-bulb-content-bar"></div>
        <div class="light-bulb-content"></div>
        <div class="light-bulb-content-redius"></div>
        <div class="light-bulb-content-redius light-bulb-content-redius-right"></div>
      </div>
    </div>
    <p class="space-name">WELCOME TO MUCHFUN SPEACE</p>
  </div>
</template>
<script setup>
import { defineProps } from 'vue';
const props = defineProps({
  switchState: Boolean
})

</script>
<style lang='scss'>
.light-switch {
  transition: all 0.5s;
  position: absolute;
  bottom: 48px;
  right: 48px;
  width: 224px;
  height: 224px;
  background-color: var(--switch-container-color);
  box-shadow:
    5px 5px 10px 5px var(--light-bulge-color),
    inset -2px -2px 5px 5px var(--light-bulge-color);
  border-radius: 40px;
  display: flex;
  justify-content: center;
  align-items: center;

  .switch-button-container {
    transition: all 0.5s;
    cursor: pointer;
    width: 75%;
    height: 75%;
    border-radius: 20px;
    background-color: var(--switch-button-container-color);
    border: 2px solid #00000060;
    position: relative;
    box-shadow: inset 0px 0px 4px 1px rgba(0, 0, 0, 0.25);

    .switch-button {
      transition: all 0.5s;
      position: relative;
      width: 100%;
      height: 90%;
      background: var(--switch-button-color);
      border-radius: 20px;
      position: absolute;
      bottom: 0px;
      left: 0px;

      .switch-light {
        position: absolute;
        top: 24px;
        left: 50%;
        transform: translateX(-50%);
        width: 48px;
        height: 12px;
        background: #ffb760;
        box-shadow: 0 0 20px #ffb760;
        border-radius: 11px;

      }
    }

    .switch-button-on {
      top: 0px;
    }
  }
}

.light-bulb-container {
  z-index: 1;
  position: absolute;
  width: 500px;
  top: -284vh;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;

  .light-bulb-line {
    transition: all 0.5s ease-out;
    background-color: var(--light-bulb-root);
    width: 12px;
    height: 300vh;
    box-shadow: inset 8px 0px 4px var(--light-bulge-color);
  }

  .light-bulb {
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;

    &::after {
      content: '';
      position: absolute;
      transition: all 0.5s ease-out;
      bottom: 10px;
      width: 200px;
      height: 200px;
      border-radius: 50%;
      filter: blur(90px);
      background-color: var(--light-bulb);
      box-shadow:
        0 0 100px var(--light-bulb),
        0 0 500px var(--light-bulb),
        0 0 1000px var(--light-bulb),
        0 0 2000px var(--light-bulb),
    }

    .light-bulb-root {
      transition: all 0.5s ease-out;
      width: 90px;
      height: 20px;
      background: var(--light-bulb-root);
      box-shadow: inset 0px 0px 7px 4px var(--light-bulge-color);
      border-radius: 20px;
    }

    .light-bulb-content-bar {
      transition: all 0.5s ease-out;
      width: 80px;
      height: 60px;
      background-color: var(--light-bulb);
    }

    .light-bulb-content-redius {
      transition: all 0.5s ease-out;
      position: absolute;
      top: 96px;
      left: 16px;
      width: 21px;
      height: 23px;
      box-shadow: 10px 10px 0 5px var(--light-bulb);
      border-bottom-right-radius: 100%;
      transform: rotate(345deg);
    }

    .light-bulb-content-redius-right {
      right: 16px;
      left: auto;
      transform: rotate(113deg);
    }

    .light-bulb-content {
      transition: all 0.5s ease-out;
      position: relative;
      top: -20px;
      width: 150px;
      height: 150px;
      background-color: var(--light-bulb);
      border-radius: 50%;
    }
  }

}

.space-name {
  transition: all 1s;
  position: absolute;
  top: 500px;
  left: 50%;
  color: var(--space-name-color);
  transform: translateX(-50%);
  font-size: 56px;
  line-height: 60px;
  font-weight: 500;
  text-shadow: var(--space-name-shadow);
}

//Here is the enter move animations
.enter-move-light {

  .light-switch {
    animation-name: switch-move;
  }

  .light-bulb-container {
    animation-name: light-bulb-move;
  }

  .light-bulb::after {
    animation-name: bulb-light-move;
  }

  .space-name {
    animation-name: space-name-move;
  }

  .light-switch,
  .light-bulb-container,
  .space-name,
  .light-bulb::after {
    animation-delay: 2s;
    animation-duration: 3s;
    animation-iteration-count: 1;
    animation-fill-mode: forwards;
  }

  @keyframes switch-move {
    50% {
      transform: scale(30%) translate(40px, 10vh);
    }

    100% {
      transform: scale(30%) translate(40px, -140vh);
    }
  }

  @keyframes light-bulb-move {
    50% {
      transform: scale(30%) translateY(400vh);
      left: 5vw
    }

    100% {
      transform: scale(30%) translateY(275vh);
      left: 5vw
    }
  }

  @keyframes space-name-move {
    50% {
      opacity: 100%;
      text-shadow: none;
    }

    100% {
      opacity: 0%;
      text-shadow: none
    }
  }

  @keyframes bulb-light-move {
    50% {
      opacity: 0%;
    }

    100% {
      opacity: 0%;
    }
  }
}
</style>
