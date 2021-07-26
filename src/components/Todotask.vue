<template>
  <div>
    <li :class="{completed: task.completed}">
      <span :class="{checked: task.completed}">
        <input type="checkbox" v-on:change ="completer()">
        <strong>{{index+1}}</strong>
        {{task.title}}
      </span>
      <div class="buttons">
        <input type="text" v-model="renameDescription"
        :class="{usable: !task.rename}">
        <button class="rename-but" 
        v-on:click ="edit(), hidder()" 
        :class="{usable: !task.rename}"><img src="~@/assets/accepted.png" class="img" alt="">
        </button>

        <button class="rename-but" 
        v-on:click ="hidder()" 
        :class="{usable: task.rename}" ><img src="~@/assets/pencil-pen.png" class="img" alt="">
        </button>

        <button class="rename-but" 
        v-on:click ="$emit('remove-todo', task.id)">&times;
        </button>
      </div>
    </li>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      requred: true,
    },
    index: Number,
  },
  data() {
    return {
      renameDescription: ''
    }
  },
  methods: {
    edit: function() {
      this.task.title = this.renameDescription;
      this.renameDescription = '';
    },
    hidder: function() {
      this.task.rename = !this.task.rename;
    },
    completer: function() {
      this.task.completed = !this.task.completed;
    }
  }
}
</script>

<style scoped>
li{
  border: 3px solid #DDE0E6;
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 50px;
  margin: 15px;
  padding: 3px;
}
.checked{
  text-decoration: line-through;
  background-color: greenyellow;
}
.completed{
  background-color: greenyellow;
}
span{
  padding: 5px;
}
.img{
  width: 12px;
}
.rename-but{
  margin-right: 10px;
  width: 30px;
  height: 30px;
}
.buttons{
  padding-right: 10px;
}
.usable{
  visibility:  hidden;
}
input{
  margin-right: 15px;
}
</style>