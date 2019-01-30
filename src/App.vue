<template>
  <div id="app">
    <TaskForm v-on:create-task="createTask" />
    <TaskList :task="task" />
  </div>
</template>

<script>
  import TaskForm from './components/TaskForm/TaskForm'
  import TaskList from './components/TaskList/TaskList'

  export default {
    name: 'App',

    components: { TaskForm, TaskList },

    data() {
      return {
        task: {}
      }
    },

    methods: {
      createTask(taskName) {
        const newTask = { name: taskName }
        fetch('http://localhost:8081/api/tasks', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify(newTask)
        })
          .then(res => res.json())
          .then(data => this.task = data)
          // eslint-disable-next-line
          .catch(err => console.log('Error [App.vue - createTask]: \n' + err))
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
