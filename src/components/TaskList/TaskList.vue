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
    name: 'TaskList',

    components: { TaskListItem },

    props: {
      task: { type: Object, required: true }
    },
    
    data() {
      return {
        tasks: []
      }
    },
    
    watch: {
      task: function (newVal) {
        this.tasks = [...this.tasks, newVal]
      }
    },

    created() {
      fetch('http://localhost:8081/api/tasks')
        .then(res => res.json())
        .then(tasks => this.tasks = [...tasks])
        // eslint-disable-next-line
        .catch(err => console.log('Error: \n' + err))
    },

    methods: {
      removeTask(taskId) {
        fetch(`http://localhost:8081/api/tasks/${ taskId }`, {
          method: 'DELETE'
        })
          .then(() => this.tasks = this.tasks.filter(task => task.id !== taskId))
          // eslint-disable-next-line
          .catch(err => console.log('Error [TaskList.vue - removeTask]: \n' + err))
      }
    },
  }
</script>

<style lang="scss" scoped>
  
</style>
