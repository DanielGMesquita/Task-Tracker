<template>
    <div class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">
                {{ task.description }}
            </div>
            <div class="column">
                <StopwatchDisplay :timeInSeconds="task.durationInSeconds"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
    import { defineComponent, PropType } from 'vue'
    import StopwatchDisplay from './Stopwatch.vue';
    import ITask from '../interfaces/ITask';

    export default defineComponent({
        name: 'TaskDetail',
        components: {
            StopwatchDisplay
        },
        props: {
            task: {
                type: Object as PropType<ITask>,
                required: true
            }
        }
    })
</script>

<style scoped>
/* scoped significa que este estilo só se aplica a este componente */
    .box{
        background: #FAF0CA;
    }
</style>