<script setup>
import { ref, onMounted} from "vue";

const hourHand = ref("");
const minuteHand = ref("");
const secondHand = ref("");

const secDeg = ref(0);
const minDeg = ref(0);
const hourDeg = ref(0);

function setClock() {
  const currentDate = new Date();
    const sec = currentDate.getSeconds();
    const min = currentDate.getMinutes();
    const hour = currentDate.getHours(); 

    secDeg.value = sec * 6;
    minDeg.value = min * 6;
    hourDeg.value = 30 * hour + min / 2;
}

  setInterval(setClock, 1000);

  setClock();


</script>

<template>
 <div class="clock-dial">
    <div class="point"></div>
    <div class="hand hour" ref="hourHand" :style="{transform: `rotate(${hourDeg}deg)`}"></div>
    <div class="hand minute" ref="minuteHand" :style="{transform: `rotate(${minDeg}deg)`}"></div>
    <div class="hand second" ref="secondHand" :style="{transform: `rotate(${secDeg}deg)`}"></div>
    <div :class='["hour num"+ i]' v-for="(n, i) in 12" :key="i" :style="`--rotation:30*${i}`">
      <span>{{n}}</span>
    </div>
 </div>
</template>

<style scoped>
  
.clock-dial {
  width: 500px;
  height: 500px;
  border: 1px solid rgb(110, 110, 110);
  border-radius: 50%;
  position: relative;
  background-color: white;
  box-shadow: rgba(0, 0, 0, 0.25) 0px 54px 55px, rgba(0, 0, 0, 0.12) 0px -12px 30px, rgba(0, 0, 0, 0.12) 0px 4px 6px, rgba(0, 0, 0, 0.17) 0px 12px 13px, rgba(0, 0, 0, 0.09) 0px -3px 5px;
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
  transform: rotate(calc(1deg * var(--rotation)));
}

.hour span {
  display: inline-block;
  transform: rotate(calc(-1deg * var(--rotation)));
}

.hand {
  position: absolute;
  bottom: 50%;
  left: 50%;
  border: 1px solid white;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  transform-origin: bottom;
  z-index: 10;
  transform: translateX(-50%);
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
