<template>
  <form @submit="createTask" >
    <TaskFormInput type="text" v-on:update-task-name-input-value="updateTaskNameInputValue" />
    <TaskFormInput type="submit" />
  </form>
</template>

<script>
  import TaskFormInput from './components/TaskFormInput/TaskFormInput'

  export default {
    name: 'TaskForm',
    components: { TaskFormInput },
    methods: {
      createTask(e) {
        e.preventDefault()
        this.$emit('create-task', this.taskName)
      },
      updateTaskNameInputValue(taskNameFromChildInput) {
        this.taskName = taskNameFromChildInput
      }
    },
    data() {
      return {
        taskName: ''
      }
    }
  }
</script>

<style>

</style>
