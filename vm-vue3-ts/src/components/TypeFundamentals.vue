<template>
  <div>
    <h2>{{ msg }}</h2>
    <ol>
      <li>String</li>
      <li>Number</li>
      <li>Boolean</li>
      <li>Array</li>
      <li>Function</li>
      <li>Object</li>
      <li>Any - esentially disables any type checking</li>
      <li>Tuple - fixed length arrays with predefined data types</li>
      <li>Enum - allows you to define friendly names to a set of values</li>
      <li>...</li>
    </ol>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Type Fundamentals",
  props: {
    msg: String
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h2, h3 {
  margin: 40px 0 0;
}
</style>
