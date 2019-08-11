<template>
  <div class="todolist">
    <ol>
      <li v-for="(listItem,index) in list" :key="index">{{listItem.name}}</li>
    </ol>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component({
  props: {
    list: Array
  }
})
export default class TodoList extends Vue {}
</script>

<style lang="scss"></style>
