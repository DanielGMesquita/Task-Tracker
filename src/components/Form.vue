<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        area-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
        />
      </div>
      <div class="column">
        <section
          class="is-flex is-align-items-center is-justify-content-space-between"
        >
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
        </section>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import StopwatchDisplay from "./Stopwatch.vue";

export default defineComponent({
  name: "FormHandler",
  components: {
    StopwatchDisplay,
  },
  //data define estados para o componente
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
