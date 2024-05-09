<script setup>




</script>

<template>
 <div class="clock-dial">
    <div class="point"></div>
    <div class="hand hour"></div>
    <div class="hand minute"></div>
    <div class="hand second"></div>
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

.point {
  width: 20px;
  height: 20px;
  background-color: black;
  border-radius: 50%;
  position: absolute;
  top: 50%;
  left: 50%;
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

</style>
