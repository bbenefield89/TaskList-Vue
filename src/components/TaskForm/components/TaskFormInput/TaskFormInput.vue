<template>
  <input :type="type" v-model="taskName" @keypress="updateTaskNameInputValue" />
</template>

<script>
  export default {
    name: 'TaskFormInput',
    methods: {
      updateTaskNameInputValue(e) {
        this.$emit('update-task-name-input-value', e.target.value)
      }
    },
    props: {
      type: String
    }
  }
</script>

<style>

</style>
