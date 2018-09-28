<template>
  <div class="container-fluid">
<section class="main-section">
  <aside>
    fff
  </aside>
    <!-- Todos Card -->
  <section class="todo-section">
    <!-- TodoInput Header -->
    <div class="main">
      <div class="header mb-1">

        <div class="d-flex justify-content-between">

          <span>
            <span class="date">{{today.getDate().toString()}}</span>
            <div>
              <span class="days">{{toMonth(today.getMonth()+1)}}</span>
              <span class="days">{{today.getFullYear()}}</span>
            </div>
          </span>

          <span>
            <h4>Todos</h4>
          </span>

        </div>

      </div>

      <!-- TodoList Content -->
      <div class="content">
        
        <div class="todo-view">
        <span class="span-button btn btn-primary"></span>
          <input type="text" v-model="todo" @keyup.enter="addTodo(todo)" autofocus="autofocus"
          class="todo-input" placeholder="What do you want to do?" />
          <span class="span-button btn btn-primary" @click="addTodo(todo)">+</span>
        </div>

        <div class="sort d-flex justify-content-around">
          <h6 class="m-0">- Items left</h6>
          <a>All</a>
          <a>Done</a>
          <a>Not Done</a>
        </div>

        <ul class="list-group">

          <li v-for="(todo, i) in todoList" v-bind:key="i" class="d-flex">
            <span class=" btn " @click="toggleCompleted(i)"></span>

            <input type="text" @dblclick.self="focus($event)" readonly v-model=todo.todoText
            @keyup.self.enter="editTodo(todo.todoText,i,$event)" v-bind:class="{completed: todo.completed}" />

            <span class="btn btn-danger" @click="deleteTodo(i)"></span>

          </li>

        </ul>

      </div>

    </div>

  </section>

</section>
  <!-- Side bar -->

  <!-- TodoList footer -->
  <footer class="col-md-12">
    <p>double click to edit, press enter to save</p>
    <p>by emmanuel-segun-lean</p>
    <p><a href="https://twitter.com/leankhan_" target="_blank">twitter</a>  <a href="https://github.com/LeanKhan" target="_blank">github</a></p>
  </footer>


  </div>
</template>

<script>
export default {
  data: function() {
    return {
      todo: "",
      todoList: [],
      today: new Date()
    };
  },
  methods: {
    addTodo: function(todoItem) {
      if (todoItem === "") {
      } else {
        this.todoList.push({
          todoText: todoItem,
          completed: false
        });
        this.todo = "";
      }
    },
    focus: function(e) {
      // e.target.readonly = !e.target.readonly
      e.target.readOnly = !e.target.readOnly;
    },
    editTodo: function(newText, id, e) {
      this.todoList[id].todoText = newText;
      this.focus(e);
    },
    deleteTodo: function(id) {
      this.todoList.splice(id, 1);
    },
    toggleCompleted: function(id) {
      this.todoList[id].completed = !this.todoList[id].completed;
    },
    toMonth: function(month) {
      switch (month) {
        case 1:
          return "January";
          break;
        case 2:
          return "February";
          break;
        case 3:
          return "March";
          break;
        case 4:
          return "April";
          break;
        case 5:
          return "May";
          break;
        case 6:
          return "June";
          break;
        case 7:
          return "July";
          break;
        case 8:
          return "August";
          break;
        case 9:
          return "September";
          break;
        case 10:
          return "October";
          break;
        case 11:
          return "November";
          break;
        case 12:
          return "December";
          break;
        default:
          return month;
      }
    }
  }
};
</script>
