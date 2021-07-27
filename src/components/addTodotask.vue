<template>
<div class="manyways">
  <form v-on:submit.prevent = "onSubmit">
    <input type="text" v-model="taskName">
    <button type="submit">Create</button>
  </form>
    <button type="submit" v-on:click="$emit('search-task', taskName)">Search</button>
</div>
</template>

<script>
export default {
  data() {
    return {
        taskName: ''
    }
  },
  methods: {
      onSubmit() {
        let newTodo = {
          id: Date.now(),
          title: this.taskName,
          completed: false,
          rename: false,
          checkbox_clicked: false,
        }
        this.$emit('add-todo', newTodo);
        this.taskName = ''
      },
    }
  }
</script>

<style>

.manyways{
  display: flex;
  justify-content: center;
}
</style>