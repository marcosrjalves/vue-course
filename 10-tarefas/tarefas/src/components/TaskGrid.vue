<template>
  <div class="task-grid">
        <template v-if="tasks.length">
            <Task v-for="(task, i) in tasks" :key="task.name"
                @taskDeleted="$emit('taskDeleted', i)"
                @taskStateChanged="$emit('taskStateChanged', i)"
                :task="task">
            </Task>
        </template>
        <p v-else class="no-task">Sua vida está em dia :)</p>
    </div>
</template>

<script>
import Task from '@/components/Task'
export default {
    components: { Task },
    props: {
        tasks: {
            type: Array,
            required: true
        }
    }

}
</script>

<style>
    .task-grid {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }

    .task-grid .task {
        margin: 10px;
    }

    .no-task {
        color: rgb(185, 255, 128);
        font-size: 1.7rem;
    }
</style>