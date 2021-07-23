<template>
  <form v-on:submit.prevent = "onSubmit">
    <input type="text" v-model="taskName">
    <button type="submit">Create</button>
  </form>
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
          completed: false
        }
        this.$emit('add-todo', newTodo);
        this.title = ''
      }
    }
  }
</script>