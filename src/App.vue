<template>
  <div id="app">
    <TaskForm v-on:create-task="createTask" />
    <TaskList :tasks="tasks" v-on:remove-task="removeTask" />
  </div>
</template>

<script>
  import TaskForm from './components/TaskForm/TaskForm'
  import TaskList from './components/TaskList/TaskList'

  export default {
    name: 'App',
    components: { TaskForm, TaskList },
    methods: {
      createTask(taskName) {
        const newTask = { id: this.tasks.length, name: taskName }
        this.tasks = [ ...this.tasks, newTask ]
      },
      removeTask(taskId) {
        this.tasks = this.tasks.filter(task => task.id !== taskId)
      }
    },
    data() {
      return {
        tasks: [{ id: 0, name: 'Task One', isComplete: false }]
      }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
