<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <Sidebar />
    </div>
    <div class="column is-three-quarter">
      <FormHandler @whenSaveTask="saveTask" />
      <div class="list">
        <TaskDetail v-for="(task, index) in tasks" :key="index"/>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Sidebar from "./components/Sidebar.vue";
import FormHandler from "./components/Form.vue";
import TaskDetail from "./components/Task.vue";
import ITask from "./interfaces/ITask"

export default defineComponent({
  name: "App",
  components: { Sidebar, FormHandler, TaskDetail},
  data () {
    return {
      tasks: [] as ITask[]
    }
  },
  methods: {
    saveTask (task: ITask) {
      this.tasks.push(task)
    }
  }
});
</script>

<style>
  .list {
    padding: 1.25rem;
  }
</style>
