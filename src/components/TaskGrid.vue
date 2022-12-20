<template>
    <div class="taskGrid" v-if="tasks.length">
        <template>
            <Task @taskStateChanged="$emit('taskStateChanged', i)" @taskDeleted="$emit('taskDeleted', i)" v-for="(task, i) in tasks" :key="task.name" :task="task" />
        </template>
    </div>
    <p v-else class="no-task"> No Tasks </p>
</template>

<script>
import Task from "./Task.vue"

export default {
    name: 'TaskGrid',
    components: {
        Task,
    },
    props: {
        tasks: {
            type: Array,
            required: true
        }
    }
}
</script>

<style scoped>
.taskGrid {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
}

.taskGrid .task {
    margin: 10px;
}

.no-task {
    color: #AAA;
    font-size: 1.7rem;
}

</style>