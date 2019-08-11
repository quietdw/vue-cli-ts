<template>
  <div class="new-todolist">
    <input v-model="message" />
    <button @click="addTodo">Add</button>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component({})
export default class NewTodoList extends Vue {
  message = "";
  addTodo() {
    this.$emit("addTodo", this.message);
    this.message = "";
  }
}
</script>

<style lang="scss"></style>
