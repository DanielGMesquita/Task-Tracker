<template>
    <div class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">
                Task Details
            </div>
            <div class="column">
                <StopwatchDisplay timeInSeconds="15"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
    import { defineComponent } from 'vue'
    import StopwatchDisplay from './Stopwatch.vue';

    export default defineComponent({
        name: 'TaskDetail',
        components: {
            StopwatchDisplay
        }
    })
</script>

<style scoped>
/* scoped significa que este estilo só se aplica a este componente */
    .box{
        background: #FAF0CA;
    }
</style>