<template>
  <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />
  <hr>
  <TypeFundamentals msg="Lesson: Type Fundamentals" />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import HelloWorld from "./components/HelloWorld.vue";
import TypeFundamentals from "./components/TypeFundamentals.vue";

export default defineComponent({
  name: "App",
  components: {
    HelloWorld,
    TypeFundamentals
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
