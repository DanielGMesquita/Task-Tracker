<template>
  <section>
    <strong> {{ timeElapsed }} </strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "StopwatchDisplay",
  //props são as propriedades que serão utilizadas e suas características
  props: {
    timeInSeconds: {
      type: Number,
      default: 0,
    },
  },
  computed: {
    timeElapsed(): string {
      return new Date(this.timeInSeconds * 1000)
        .toISOString()
        .substring(11, 19);
    },
  },
});
</script>
