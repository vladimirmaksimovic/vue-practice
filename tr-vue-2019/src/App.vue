<template>
  <div id="app" class="small-container">
    <img alt="Vue logo" src="@/assets/logo.png" />
    <h1>Employees</h1>

    <employee-table />
  </div>
</template>

<script>
import EmployeeTable from "@/components/EmployeeTable.vue";

export default {
  name: "app",
  components: {
    EmployeeTable,
  },
};
</script>

<style>
.small-container {
  max-width: 680px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.small-container img {
  width: 20%;
  margin: 2rem auto;
  padding: 0.5rem;
  border-radius: 50%;
  border: 3px dotted #009435;
}

button {
  background: #009435;
  border: 1px solid #009435;
}
</style>
