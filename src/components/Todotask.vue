<template>
  <div>
    <li>
      <span :class="{checked: todo.completed}">
        <input type="checkbox" v-on:change="todo.completed = !todo.completed">
        <strong>{{todo.id}}</strong>
        {{todo.title}}
      </span>
      <button v-on:click="$emit('remove-todo', todo.id)">&times;</button>
    </li>
  </div>
</template>

<script>
export default {
  props: {
    todo: {
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