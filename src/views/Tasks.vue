<template>
  <FormHandler @whenSaveTask="saveTask" />
  <div class="list">
    <TaskDetail v-for="(task, index) in tasks" :key="index" :task="task" />
    <BoxTemplate v-if="emptyList">
      Nenhuma tarefa em acompanhamento.
    </BoxTemplate>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import FormHandler from "../components/Form.vue";
import TaskDetail from "../components/Task.vue";
import ITask from "../interfaces/ITask";
import BoxTemplate from "../components/Box.vue";

export default defineComponent({
  name: "App",
  components: { FormHandler, TaskDetail, BoxTemplate },
  data() {
    return {
      tasks: [] as ITask[],
    };
  },
  computed: {
    emptyList(): boolean {
      return this.tasks.length === 0;
    },
  },
  methods: {
    saveTask(task: ITask) {
      this.tasks.push(task);
    },
  },
});
</script>