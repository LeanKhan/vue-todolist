<template>
  <div class="container">
    <h2>Place your todos here!</h2>
    <h4>{{today.toLocaleDateString()}}</h4>
    <input type="text" :placeholder= "todo" v-model="todo" @keyup.enter="addTodo(todo)">
   
    <button class="addTodo"  @click="addTodo(todo)">Add todo</button>
    <ul>
      <li v-for="(todo, i) in todoList" v-bind:key="i">
      <a @click="toggleCompleted(i)">done</a>
       <span>{{i}}</span> <input type="text" @dblclick.self="focus($event)" readonly v-model=todo.todoText @keyup.self.enter="editTodo(todo.todoText,i,$event)" v-bind:class="{completed: todo.completed}">
       <a @click="deleteTodo(i)">delete</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      todo: "",
      todoList: [],
      today: new Date(),
    };
  },
  methods: {
    addTodo: function(todoItem) {
      if(todoItem === ""){alert("Can't do that bro!")
      }else{
       this.todoList.push({
        todoText: todoItem,
        completed: false,
        });
      this.todo = "";
      }
    },
    focus: function(e){
      // e.target.readonly = !e.target.readonly
      e.target.readOnly = !e.target.readOnly;
    },
    editTodo: function(newText,id,e){
      this.todoList[id].todoText = newText;
      this.focus(e);
    },
    deleteTodo: function(id){
      this.todoList.splice(id,1);
    },
    toggleCompleted: function(id){
      this.todoList[id].completed = !this.todoList[id].completed
    }
  }
};
</script>

<style scoped>
  ul {
    list-style-type: none;
  }
  a {
   padding: 5px;
    cursor: pointer !important;
  }
  a:hover {
    text-decoration: underline;
  }
  .completed {
    text-decoration: line-through !important;
    color: gray;
  }
</style>

