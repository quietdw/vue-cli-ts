<template>
  <div id="app">
    <NewTodoList @addTodo="addTodo"></NewTodoList>
    <TodoList :list="list" @changeStatus="changeStatus"></TodoList>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Mixins } from "vue-property-decorator";
import NewTodoList from "./components/NewTodoList.vue";
import TodoList from "./components/TodoList.vue";
import Todo from "./models/Todo";

@Component({
  components: { NewTodoList, TodoList },
  watch: {
    list(oldValue, newValue) {
      localStorage.setItem("data", JSON.stringify(newValue));
    }
  }
})
export default class App extends Vue {
  list: Array<Todo> = localStorage.getItem("data")
    ? JSON.parse(<string>localStorage.getItem("data"))
    : [];
  addTodo(message: String) {
    let todo: Todo = { name: message, status: "todo" };
    this.list.push(todo);
  }
  changeStatus(listItem: Todo, index: number, status: Partial<Todo>) {
    let newList = Object.assign({}, listItem, status);

    this.list.splice(index, 1, newList);
  }
}
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
}
</style>
