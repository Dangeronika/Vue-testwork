<template>
  <div id="app">
    <Todohead/>
    <AddTodotask v-on:add-todo='addTodo'/>
    <Todolist :tasks = 'tasks' class="list"
    v-if="tasks.length"
    @remove-todo='remove'/>
    <p v-else> No tasks! </p>
  </div>
</template>

<script>

import Todohead from '@/components/Todohead'
import Todolist from '@/components/Todolist'
import AddTodotask from '@/components/addTodotask'
export default {
  name: "App",
  data() {
    return {
      tasks: [
        {id: 1, title: 'ananas', completed:false, rename:false},   
      ],
    }
  },
  components: {
    Todohead,
    Todolist,
    AddTodotask,
  },
  methods: {
    remove(id) {
      this.tasks = this.tasks.filter( t => t.id !==id)
    },
    addTodo(newTodo) {
      this.tasks.push(newTodo)
    }
  }
};
</script>

<style>
.list{
  margin-top: 50px;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
