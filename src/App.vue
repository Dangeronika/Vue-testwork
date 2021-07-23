<template>
  <div id="app">
    <Todohead/>
    <AddTodotask v-on:add-todo='addTodo'/>
    <Todolist :tasks = 'tasks' class="list"
    @remove-todo='remove'/>
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
        {id: 1, title: 'ananas', completed:false},
        {id: 2, title: 'abrikos', completed:false},
        {id: 3, title: 'arbuz', completed:false},
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
