<template>
  <div class="box has-text-weight-bold">
    <slot></slot>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "BoxTemplate",
});
</script>

<style scoped>
/* scoped significa que este estilo só se aplica a este componente */
.box {
  background: #faf0ca;
}
</style>
