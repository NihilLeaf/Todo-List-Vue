<template>
  <div id="app">
    <h1>Tasks</h1>
    <TaskGrid :tasks="tasks" />
  </div>
</template>

<script>
import TaskGrid from "./components/TaskGrid"

export default {
  name: 'App',
  components: {
    TaskGrid,
  },
  data() {
    return {
      tasks: [
        {name: 'lavar louça', pending: false},
        {name: 'Comprar Sapato', pending: true}
      ]
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
  color: #bf7329;
}
</style>
