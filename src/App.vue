<template>
  <div id="app">
    <h1>Tasks</h1>
    <NewTask @taskAdded="addTask" />
    <TaskGrid @taskStateChanged="toggleState" @taskDeleted="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import TaskGrid from "./components/TaskGrid"
import NewTask from "./components/NewTask.vue"

export default {
  name: 'App',
  components: {
    TaskGrid,
    NewTask,
  },
  data() {
    return {
      tasks: []
    }
  },
  methods: {
    addTask(task) {
      const SAMENAME = t => t.name === task.name
      const REALLYNEW = this.tasks.filter(SAMENAME).length == 0
      if (REALLYNEW) {
        this.tasks.push({
          name: task.name,
          pending: task.pending || true
        })
      }
    },
    deleteTask(i) {
      this.tasks.splice(i, 1)
    },
    toggleState(i) {
      this.tasks[i].pending = !this.tasks[i].pending
    }
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: 'Ubuntu', sans-serif;
  display: flex;
  flex: 1;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background-image: linear-gradient(to right, #0d1226,
      #3d2e22);
  overflow-x: hidden;
  color:
    #ff4e20;
}
</style>
