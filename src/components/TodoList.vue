<template>
  <div class="todolist">
    <ol>
      <li v-for="(listItem,index) in list" :key="index">
        <input
          type="checkbox"
          :checked="listItem.status==='done'"
          @change="changeStatus(listItem,index,$event)"
        />
        {{listItem.name}}
      </li>
    </ol>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import Todo from "../models/Todo";

@Component({
  props: {
    list: Array
  }
})
export default class TodoList extends Vue {
  changeStatus(listItem: Todo, index: number, e: Event) {
    this.$emit("changeStatus", listItem, index, {
      status: (<HTMLInputElement>e.target).checked ? "done" : "undo"
    });
  }
}
</script>

<style lang="scss"></style>
