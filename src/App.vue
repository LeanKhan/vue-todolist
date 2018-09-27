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
   addTodo,
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
