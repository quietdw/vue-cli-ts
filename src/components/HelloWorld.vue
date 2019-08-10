<template>
  <div class="hello">hello,{{name}}</div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component({
  props: {
    name: String
  }
})
export default class HelloWorld extends Vue {}
</script>
