<template>
  <button @click="removeTask">X</button>
</template>

<script>
  export default {
    name: 'RemoveTaskListItemButton',
    methods: {
      removeTask() {
        this.$emit('remove-task')
      }
    }
  }
</script>

<style>

</style>
