<template>
  <li>
    <TaskListItemName :taskName="task.name" />
    <RemoveTaskListItemButton v-on:remove-task="removeCharacter" />
  </li>
</template>

<script>
  import TaskListItemName from '../TaskListItemName/TaskListItemName'
  import RemoveTaskListItemButton from '../RemoveTaskListItemButton/RemoveTaskListItemButton'

  export default {
    name: 'TaskListItem',
    components: { TaskListItemName, RemoveTaskListItemButton },
    methods: {
      removeCharacter() {
        this.$emit('remove-task')
      }
    },
    props: {
      task: Object
    }
  }
</script>

<style>

</style>
