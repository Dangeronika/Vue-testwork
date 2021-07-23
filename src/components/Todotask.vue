<template>
  <div>
    <li>
      <span :class="{checked: task.completed}">
        <input type="checkbox" v-on:change="task.completed = !task.completed">
        <strong>{{task.id}}</strong>
        {{task.title}}
      </span>
      <button v-on:click="$emit('remove-todo', task.id)">&times;</button>
    </li>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      requred: true,
    }
  }
  
}
</script>

<style scoped>
li{
  border: 3px solid #DDE0E6;
  display: flex;
  justify-content: space-between;
  padding: 15px;
}

.checked{
  text-decoration: line-through;
}
</style>