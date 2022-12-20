<template>
    <div @click="$emit('taskStateChanged', task)" class="task" :class="stateClass">
        <span @click.stop="$emit('taskDeleted', task)" class="close">x</span>
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
    position: relative;
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

.pending .close {
    background-color: #913228;
}

.done .close {
    background-color: #203838;
}

.close {
    position: absolute;
    right: 10px;
    top: 10px;
    font-size: 0.9rem;
    font-weight: 600;
    height: 20px;
    width: 20px;
    border-radius: 10px;
    display: flex;
    justify-content: center;
}

</style>