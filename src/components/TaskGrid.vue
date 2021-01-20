<template>
    <div class="task-grid">
        <template v-if="tasks.length">
            <Task :task="task" v-for="(task, i) in tasks" :key="task.name" 
            @deletedTask="$emit('deletedTask', i)"
            @taskStateChanged="$emit('taskStateChanged', i)"
            ></Task>
        </template>    
        <p v-else class="no-task">Sua vida está em dia :)</p>
    </div>
</template>

<script>
import Task from './Task.vue'

export default {
    props: {
        tasks: {
            type: Array,
            required: true
        }
    },
    components: {
        Task
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
        color: #AAA;
        font-size: 1.7rem;
    }
</style>