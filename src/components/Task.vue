<template>
  <BoxTemplate>
    <div class="columns">
      <div class="column is-7">
        {{ task.description || "Tarefa sem descrição" }}
      </div>
      <div class="column">
        <StopwatchDisplay :timeInSeconds="task.durationInSeconds" />
      </div>
    </div>
  </BoxTemplate>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import StopwatchDisplay from "./Stopwatch.vue";
import ITask from "../interfaces/ITask";
import BoxTemplate from "./Box.vue";

export default defineComponent({
  name: "TaskDetail",
  components: {
    StopwatchDisplay,
    BoxTemplate,
  },
  props: {
    task: {
      type: Object as PropType<ITask>,
      required: true,
    },
  },
});
</script>


