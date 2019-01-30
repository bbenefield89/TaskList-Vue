<template>
  <div>
    <form class="task_form" @submit="createTask" >
      <input class="task_form__text_input" type="text" v-model="taskName" placeholder="New Task Name" />
      <input class="task_form__submit_input" type="submit" value="Create Task 🛫" />
    </form>
  </div>
</template>

<script>
  export default {
    name: 'TaskForm',

    data() {
      return {
        taskName: ''
      }
    },

    methods: {
      createTask(e) {
        e.preventDefault()
        this.$emit('create-task', this.taskName)
        this.taskName = ''
      },

      updateTaskNameInputValue(taskNameFromChildInput) {
        this.taskName = taskNameFromChildInput
      }
    },
  }
</script>

<style lang="scss" scoped>
  div {
    display: flex;
    justify-content: center;

    .task_form {
      display: flex;
      flex-direction: column;
      justify-content: space-evenly;
      width: 25%;
      
      .task_form__text_input {
        border: none;
        border-bottom: 1px solid;
        margin-bottom: 0.5rem;
        padding: 6px;
      }

      .task_form__submit_input {
        border: none;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
        cursor: pointer;
        font-size: 20px;
        outline: none;
        padding: 6px;
        position: relative;
        transform: all 0.15s;

        &:active {
          box-shadow: inset 0px 2px 4px rgba(0, 0, 0, 0.3);
          top: 4px;
        }
      }
    }
  }
</style>
