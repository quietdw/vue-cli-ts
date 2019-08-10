<template>
  <div id="app">
    <HelloWorld name="xxxxxx"></HelloWorld>
    {{msg}}
    {{mixinvalue}}
    <button @click="xxx">点击</button>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Mixins } from "vue-property-decorator";
import HelloWorld from "./components/HelloWorld.vue";
import { MyMixin } from "./mixins/mixin-one";

@Component({
  components: { HelloWorld }
})
export default class App extends Mixins(MyMixin) {
  msg = 123;
  xxx() {
    this.msg = 1;
  }
}
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;

  color: red;
}
</style>
