<template>
<div class="manyways">
  <form v-on:submit.prevent = "onSubmit">
    <input type="text" v-model="taskName">
    <button type="submit">Create</button>
  </form>
  <form v-on:submit.prevent = "search">
    <button type="submit">Search</button>
  </form>
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
        }
        this.$emit('add-todo', newTodo);
        this.taskName = ''
      }
    }
  }
</script>

<style>

.manyways{
  display: flex;
  justify-content: center;
}
</style>