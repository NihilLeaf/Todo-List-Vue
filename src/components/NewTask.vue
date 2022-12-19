<template>
    <div class="new-task">
        <input class="form-element" placeholder="New task..." v-model="name" @keydown.enter="add" type="text">
        <button class="form-element" @click="add">+</button>
    </div>
</template>

<script>
export default {
    name: 'NewTask',
    data() {
        return {
            name: ''
        }
    },
    methods: {
        add() {
            this.$emit('taskAdded', { name: this.name })
            this.name = ''
        }
    }

}
</script>

<style scoped>
.new-task {
    margin: 35px;
}

::placeholder {
    color: #ff4e20;
    opacity: 0.3;
    font-size: 1.5rem;
}

.form-element {
    outline: none;
    font-size: 2rem;
    border: 1px solid #8b5121;
    color: #ff4e20;
    padding: 5px 10px 8px;
}

input.form-element {
    width: 500px;
    background-color: rgba(20, 20, 20, 0.2);
    border-top-left-radius: 8px;
    border-bottom-left-radius: 8px;
}

button.form-element {
    border-left: none;
    background-color: rgba(20, 20, 20, 0.2);
    border-top-right-radius: 8px;
    border-bottom-right-radius: 8px;
}
</style>