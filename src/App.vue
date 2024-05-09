<script setup>
import { ref, onMounted, reactive } from "vue";

const hourHand = ref("");
const minuteHand = ref("");
const secondHand = ref("");
const currentDate = ref(new Date());


function setRotation(element,rotationRatio) {
  return reactive({
    '--rotation': rotationRatio.value * 360
  })
}
onMounted(() => {
  setInterval(() => {

    currentDate.value = new Date();
    const secondsRatio = currentDate.value.getSeconds() / 60;
    const minutesRatio = (secondsRatio + currentDate.value.getMinutes()) / 60;
    const hoursRatio = (minutesRatio + currentDate.value.getHours()) / 12; 

    setRotation(secondHand.value, secondsRatio);
    setRotation(minuteHand.value, minutesRatio);
    setRotation(hourHand.value, hoursRatio);

    
  }, 1000);
});


</script>

<template>
 <div class="clock-dial">
    <div class="point"></div>
    <div class="hand hour" ref="hourHand" :style="setRotation"></div>
    <div class="hand minute" ref="minuteHand" :style="setRotation"></div>
    <div class="hand second" ref="secondHand" :style="setRotation"></div>
    <div class="hour" v-for="(n, i) in 12" :key="i" :class='["num"+ i]'>{{n}}</div>
 </div>
</template>

<style scoped>
  

.clock-dial {
  width: 500px;
  height: 500px;
  border: 1px solid black;
  border-radius: 50%;
  position: relative;
  background-color: white;
}

.clock-dial::after {
  content: '';
  position: absolute;
  background-color: black;
  z-index: 11;
  width: 15px;
  height: 15px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  border-radius: 50%;
}

.hour {
  --rotation: 0;
  font-size: 3rem;
  font-weight: bold;
  color: black;
  position: absolute;
  width: 100%;
  height: 100%;
  text-align: center;
  transform: rotate(var(--rotation));
}

.num0 {--rotation: 30deg}

.num1 {--rotation: 60deg}

.num2 {--rotation: 90deg}

.num3 {--rotation: 120deg}

.num4 {--rotation: 150deg}

.num5 {--rotation: 180deg}

.num6 {--rotation: 210deg}

.num7 {--rotation: 240deg}

.num8 {--rotation: 270deg}

.num9 {--rotation: 300deg}

.num10 {--rotation: 330deg}

.hand {
  --rotation: 0;
  position: absolute;
  bottom: 50%;
  left: 50%;
  border: 1px solid white;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  transform-origin: bottom;
  z-index: 10;
  transform: translateX(-50%) rotate(calc(var(--rotation) * 1deg));
}

.hand.second {
  width: 5px;
  height: 45%;
  background-color: red;
}

.hand.minute {
  width: 7px;
  height: 40%;
  background-color: black;
}

.hand.hour {
  width: 10px;
  height: 35%;
  background-color: black;
}


</style>
