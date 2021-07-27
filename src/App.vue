<template>
  <div id="app">
    <Todohead/>
    <AddTodotask v-on:add-todo='addTodo' v-on:search-task="searchTask"/>
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
        {id: 1, title: 'Make a todo list', completed:false, rename: false, checkbox_clicked: false},
        {id: 2, title: 'Refactor the code', completed:false, rename: false, checkbox_clicked: false},
        {id: 3, title: 'Done the work', completed:false, rename: false, checkbox_clicked: false}
      ],
      search_flag: true,
      copyTasks: null,
    }
  },
  mounted() {
    this.getTasks();
  },
  components: {
    Todohead,
    Todolist,
    AddTodotask,
  },
  methods: {
    remove(id) {
      this.tasks = this.tasks.filter( t => t.id !==id )
    },
    addTodo(newTodo) {
      this.tasks.push(newTodo);
    },
    searchTask(taskName) {

      if(this.search_flag) {
        this.copyTasks = this.tasks.slice()
        this.search_flag = false;
      }

      if(taskName !=''){
        this.tasks = this.tasks.filter( t => t.title == taskName);
      } else {
        this.tasks = this.copyTasks.slice();
        this.search_flag = true;
      }
    },
    getTasks() {
      if (localStorage.getItem('tasks')) {
        this.tasks = JSON.parse(localStorage.getItem('tasks'));
      }
    },
  },
  watch: {
    tasks: {
      handler: function(updateTasks) {
        localStorage.setItem('tasks', JSON.stringify(updateTasks));
      },
      deep:true
    }
  },
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
