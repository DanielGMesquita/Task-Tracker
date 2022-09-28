<template>
  <div class="box form">
    <div class="columns">
      <div
        class="column is-5"
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
      <div class="column is-3">
        <div class="select">
          <select v-model="projectId">
            <option value="">Selecione o projeto</option>
            <option
              :value="project.id"
              v-for="project in projects"
              :key="project.id"
            >
              {{ project.name }}
            </option>
          </select>
        </div>
      </div>
      <div class="column">
        <section
          class="is-flex is-align-items-center is-justify-content-space-between"
        >
          <StopwatchControls @finishedStopwatch="endTask" />
        </section>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { key } from "@/store";
import { computed } from "@vue/reactivity";
import { defineComponent } from "vue";
import { useStore } from "vuex";
import StopwatchControls from "./StopwatchControl.vue";

export default defineComponent({
  name: "FormHandler",
  emits: ["whenSaveTask"],
  components: {
    StopwatchControls,
  },
  data() {
    return {
      taskDescription: "",
      projectId: ""
    };
  },
  methods: {
    endTask(timeElapsed: number): void {
      this.$emit("whenSaveTask", {
        durationInSeconds: timeElapsed,
        description: this.taskDescription,
        project: this.projects.find(proj => proj.id == this.projectId)
      });
      this.taskDescription = "";
    },
  },
  setup() {
    const store = useStore(key);
    return {
      projects: computed(() => store.state.projects)
    }
  }
});
</script>

<style>
.form{
  color: var(--txt-primary);
  background: var(--bg-primary);
}
</style>