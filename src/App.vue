<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <Sidebar />
    </div>
    <div class="column is-three-quarter">
      <FormHandler @whenSaveTask="saveTask" />
      <div class="list">
        <TaskDetail v-for="(task, index) in tasks" :key="index" :task="task" />
        <BoxTemplate v-if="emptyList"> Nenhuma tarefa em acompanhamento. </BoxTemplate>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Sidebar from "./components/Sidebar.vue";
import FormHandler from "./components/Form.vue";
import TaskDetail from "./components/Task.vue";
import ITask from "./interfaces/ITask";
import BoxTemplate from "./components/Box.vue";

export default defineComponent({
  name: "App",
  components: { Sidebar, FormHandler, TaskDetail, BoxTemplate },
  data() {
    return {
      tasks: [] as ITask[],
    };
  },
  computed: {
    emptyList () : boolean {
      return this.tasks.length === 0
    }
  },
  methods: {
    saveTask(task: ITask) {
      this.tasks.push(task);
    },
  },
});
</script>

<style>
.list {
  padding: 1.25rem;
}
</style>
