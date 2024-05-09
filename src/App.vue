<script setup>
import { ref, onMounted } from "vue"

const top = ref(0);
const left = ref(0);

function position() {
  return reactive({
      top: `${this.top}px`,
      left: `${this.left}px`
  })
}

function calckHourPosition() {
  top.value = 5
  left.value = 25
}

onMounted(() => {
  calckHourPosition();
});

</script>

<template>
 <div class="clock-dial">
    <div class="point"></div>
    <div class="hour" v-for="(n, i) in 12" :key="i" :style="position">{{n}}</div>
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
  font-size: 3rem;
  font-weight: bold;
  color: black;
  
}

</style>
