<template>
  <li>
    <div>{{ index }} <slot></slot>
      <button @click="deleteTask(index)">X</button>
    </div>
    <small>{{ task.dueDate }} @ {{ task.dueTime }}</small>
  </li>
</template>

<script>
export default {
  props: ['task', 'index']
}
</script>

<style>

</style>
