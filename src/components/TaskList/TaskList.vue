<template>
  <ul>
    <TaskListItem
      v-for="task of tasks"
      v-on:remove-task="removeTask(task.id)"
      :key="task.id"
      :task="task"
    />
  </ul>
</template>

<script>
  import TaskListItem from '../TaskListItem/TaskListItem'

  export default {
    name: 'TaskName',
    components: { TaskListItem },
    methods: {
      removeTask(taskId) {
        this.$emit('remove-task', taskId)
      }
    },
    props: {
      tasks: Array
    }
  }
</script>

<style>

</style>
