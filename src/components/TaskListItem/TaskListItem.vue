<template>
  <li>
    <TaskListItemName :taskName="task.name" />
    <RemoveTaskListItemButton v-on:remove-task="removeTask" />
  </li>
</template>

<script>
  import TaskListItemName from '../TaskListItemName/TaskListItemName'
  import RemoveTaskListItemButton from '../RemoveTaskListItemButton/RemoveTaskListItemButton'

  export default {
    name: 'TaskListItem',

    components: { TaskListItemName, RemoveTaskListItemButton },

    props: {
      task: { type: Object, required: true }
    },

    methods: {
      removeTask() {
        this.$emit('remove-task')
      }
    },
  }
</script>

<style>

</style>
