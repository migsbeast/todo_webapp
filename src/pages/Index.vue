<template>
  <q-page padding>
    <ul>
      <task
      v-for="(task, index) in tasks"
      :key="task.id"
      :task="task"
      :index="index">{{ task.name }}</task>
    </ul>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      tasks: [
        {
          id: 1,
          name: 'Go to shop',
          dueDate: '2020/06/12',
          dueTime: '06:30PM'
        },
        {
          id: 2,
          name: 'Get bananas',
          dueDate: '2020/06/12',
          dueTime: '06:30PM'
        },
        {
          id: 3,
          name: 'Get apples',
          dueDate: '2020/06/12',
          dueTime: '06:30PM'
        }
      ]
    }
  },
  methods: {
    deleteTask (index) {
      this.tasks.splice(index, 1)
    }
  },
  components: {
    task: require('components/Task.vue').default
  }
}

</script>

<style>
  .border-grey {
    border : 1px solid grey;
  }
  .error{
    color: red;
    background-color: pink;
  }
</style>
