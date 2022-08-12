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
          <StopwatchControls />
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
  components: {
    StopwatchControls,
  },
});
</script>
