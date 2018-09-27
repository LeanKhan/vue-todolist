<template>
  <div class="container">

  <!-- Side bar -->
  <aside>
  
  </aside>

  <!-- Todos Card -->
  <main>
    <!-- TodoInput Header -->
    <div class="header">

      <div class="col-12">
        <h4>Time and Date</h4>
        <span></span>
      </div>

      <div class="col-12">
        <input type="text" v-model="todo" @keyup.enter="addTodo(todo)" class="todo-input" />
        <button class="addTodo"  @click="addTodo(todo)"><h3>add</h3></button>
      </div>

    </div>

    <!-- TodoList Content -->
    <div class="content">
      <ul>
      
        <li v-for="(todo, i) in todoList" v-bind:key="i" >
        <input type="checkbox" @click="toggleCompleted(i)" />

        <input type="text" @dblclick.self="focus($event)" readonly v-model=todo.todoText class="todo-input"
        @keyup.self.enter="editTodo(todo.todoText,i,$event)" v-bind:class="{completed: todo.completed}" />

        <a @click="deleteTodo(i)">x</a>

        </li>

      </ul>
    </div>

    <!-- TodoList footer -->
    <footer>
    </footer>

  </main>
    
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
.todo-input {
  font-size: 24px;
}
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
  aside {
    margin: 20px;
  }
  input[type="checkbox"] {
    width: 25px;
    height: 25px;
    outline: none;
  }
</style>

