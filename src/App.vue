<template>
  <div id="app">
    <addTodo/>
  </div>
</template>

<script>
import addTodo from "./components/add-todo";

export default {
  name: "App",
  components: {
    addTodo
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #f5f5f5;
  margin-top: 60px;
}

body {
  background-color: #253238 !important;
}
</style>
