<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-7"
        role="form"
        area-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="taskDescription"
        />
      </div>
      <div class="column">
        <section
          class="is-flex is-align-items-center is-justify-content-space-between"
        >
          <StopwatchControls @finishedStopwatch="endTask"/>
        </section>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import StopwatchControls from "./StopwatchControl.vue";

export default defineComponent({
  name: "FormHandler",
  emits: ['whenSaveTask'],
  components: {
    StopwatchControls,
  },
  data () {
    return {
      taskDescription: ''
    }
  },
  methods: {
    endTask (timeElapsed: number) : void {
      this.$emit('whenSaveTask', {
        durationInSeconds: timeElapsed,
        description: this.taskDescription
      })
      this.taskDescription = ''
    }
  }
});
</script>
