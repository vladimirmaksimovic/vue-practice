<template>
  <div id="app" class="small-container">
    <img alt="Vue logo" src="@/assets/logo.png" />
    <h1>Employees</h1>

    <!-- v-bind: - pass data as prop to child component -->
    <employee-table v-bind:employees="employees" />
  </div>
</template>

<script>
import EmployeeTable from "@/components/EmployeeTable.vue";

export default {
  name: "app",
  components: {
    EmployeeTable,
  },
  data() {
    return {
      /* data array */
      employees: [
        {
          id: 1,
          name: "Richard Hendricks",
          email: "richard@piedpiper.com",
        },
        {
          id: 2,
          name: "Bertram Gilfoyle",
          email: "gilfoyle@piedpiper.com",
        },
        {
          id: 3,
          name: "Dinesh Chugtai",
          email: "dinesh@piedpiper.com",
        },
      ],
    };
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
