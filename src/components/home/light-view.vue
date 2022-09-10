<template>
  <div class='light-view' :class="{'light-on':state.switchActive,'light-off':!state.switchActive}">
    <div class="light-switch">
      <div class="switch-button-container">
        <div class="switch-button" :class="{'switch-button-on':state.switchActive}" @click="switchClick()">
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
      <p class="space-name">WELCOME TO MUCHFUN SPEACE</p>
    </div>
  </div>
</template>
<script setup>
import { reactive } from 'vue';

const state = reactive({
  switchActive: false,
})
function switchClick() {
  state.switchActive = !state.switchActive
}
</script>
<style lang='scss'>
.light-off {
  --light-bulb: #000;
  --light-background: #000;
  --light-bulb-root: #000;
  --light-bulge-color: #00000000;
  --space-name-shadow: 0 0px 10px rgb(0, 0, 0);
  --switch-container-color: #ffffff4d;
  --switch-button-color: #ffffff1f;
  --switch-button-container-color: #8a8a8a30;
}

.light-on {
  --light-bulb: #ffffff;
  --light-background: #3f3f3f;
  --light-bulb-root: #D9D9D9;
  --light-bulge-color: #00000040;
  --space-name-shadow: 0 10px 10px rgb(0, 0, 0);
  --switch-container-color: #fff;
  --switch-button-color: #fff;
  --switch-button-container-color: #8a8a8a99;
}

.light-view {
  height: 100%;
  width: 100%;
  background-color: var(--light-background);
  position: relative;
  transition: all 0.5s ease-out;
}


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
  position: absolute;
  width: 500px;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;

  .light-bulb-line {
    transition: all 0.5s ease-out;
    background-color: var(--light-bulb-root);
    width: 12px;
    height: 120px;
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
      bottom: -50px;
      width: 300px;
      height: 300px;
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

  .space-name {
    transition: all 1s;
    margin-top: 96px;
    text-align: center;
    font-size: 48px;
    line-height: 60px;
    font-weight: 500;
    text-shadow: var(--space-name-shadow);
  }
}
</style>
