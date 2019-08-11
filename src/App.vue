<template>
  <div id="app">
    <NewTodoList @addTodo="addTodo"></NewTodoList>
    <TodoList :list="list"></TodoList>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Mixins } from "vue-property-decorator";
import NewTodoList from "./components/NewTodoList.vue";
import TodoList from "./components/TodoList.vue";

interface Todo {
  name: String;
  status: "done" | "todo" | "delete";
}

@Component({
  components: { NewTodoList, TodoList }
})
export default class App extends Vue {
  list: Array<Todo> = [
    { name: "任务1", status: "todo" },
    { name: "任务2", status: "done" },
    { name: "任务3", status: "delete" }
  ];
  addTodo(message: String) {
    let todo: Todo = { name: message, status: "todo" };
    this.list.push(todo);
  }
}
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
}
</style>
