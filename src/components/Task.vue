<template>
    <div class="task" :class="stateClass">
        <p>{{ task.name }}</p>
    </div>
</template>

<script>
export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Task',
    props: {
        task: {
            type: Object,
            required: true
        }
    },
    computed: {
        stateClass() {
            return {
                pending: this.task.pending,
                done: !this.task.pending
            }
        }
    }
}
</script>

<style scoped>
.task {
    width: 350px;
    height: 150px;
    padding: 10px;
    border-radius: 8px;
    font-size: 2rem;
    font-weight: 300;
    cursor: pointer;
    user-select: none;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
}

.pending {
    border-left: 12px solid 
    #913228;
    background-color:#c73131;
}

.done {
    color: aliceblue;
    border-left: 12px solid #203838;
    background-color: #006442;
    text-decoration: line-through;
}

</style>