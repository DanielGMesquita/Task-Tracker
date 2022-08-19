<template>
  <StopwatchDisplay :timeInSeconds="timeInSeconds" />
  <button class="button" @click="startStopwatch" :disabled="stopwatchRunning">
    <span class="icon">
      <i class="fas fa-play"></i>
    </span>
    <span>play</span>
  </button>
  <button class="button" @click="endStopwatch" :disabled="!stopwatchRunning">
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
  emits: ["finishedStopwatch"],
  components: {
    StopwatchDisplay,
  },
  data() {
    return {
      timeInSeconds: 0,
      stopwatch: 0, //referência para o intervalo (setInterval), assim podemos utilizar no clearInterval
      stopwatchRunning: false,
    };
  },
  methods: {
    startStopwatch() {
      this.stopwatchRunning = true;
      this.stopwatch = setInterval(() => {
        this.timeInSeconds += 1;
      }, 1000);
    },
    endStopwatch() {
      this.stopwatchRunning = false;
      clearInterval(this.stopwatch);
      this.$emit("finishedStopwatch", this.timeInSeconds);
      this.timeInSeconds = 0;
    },
  },
});
</script>
