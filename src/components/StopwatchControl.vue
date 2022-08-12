<template>
  <StopwatchDisplay :timeInSeconds="timeInSeconds" />
  <button class="button" @click="startStopwatch">
    <span class="icon">
      <i class="fas fa-play"></i>
    </span>
    <span>play</span>
  </button>
  <button class="button" @click="endStopwatch">
    <span class="icon">
      <i class="fas fa-stop"></i>
    </span>
    <span>stop</span>
  </button>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import StopwatchDisplay from "./Stopwatch.vue";

export default defineComponent({
  name: "StopwatchControls",
  components: {
    StopwatchDisplay,
  },
  data() {
    return {
      timeInSeconds: 0,
      stopWatch: 0, //referência para o intervalo (setInterval), assim podemos utilizar no clearInterval
    };
  },
  methods: {
    startStopwatch() {
      this.stopWatch = setInterval(() => {
        this.timeInSeconds += 1;
      }, 1000);
    },
    endStopwatch() {
      clearInterval(this.stopWatch);
    },
  },
});
</script>
