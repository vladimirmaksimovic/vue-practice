<template>
  <div id="app" class="small-container">
    <img alt="Vue logo" src="@/assets/logo.png" />
    <h1>Employees</h1>

    <employee-form v-on:add:employee="addEmployee" />

    <!-- v-bind: - pass data as prop to child component -->
    <employee-table
      v-bind:employees="employees"
      @delete:employee="deleteEmployee"
      @edit:employee="editEmployee"
    />
  </div>
</template>

<script>
import EmployeeTable from "@/components/EmployeeTable.vue";
import EmployeeForm from "@/components/EmployeeForm.vue";

export default {
  name: "app",
  components: {
    EmployeeTable,
    EmployeeForm,
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
  methods: {
    addEmployee(employee) {
      /* this.employees = [...this.employees, employee] */
      const lastId =
        this.employees.length > 0
          ? this.employees[this.employees.length - 1].id
          : 0;
      const id = lastId + 1;
      const newEmployee = { ...employee, id };

      this.employees = [...this.employees, newEmployee];
    },

    deleteEmployee(id) {
      this.employees = this.employees.filter((employee) => employee.id !== id);
    },

    editEmployee(id, updatedEmployee) {
      this.employees = this.employees.map((employee) =>
        employee.id === id ? updatedEmployee : employee
      );
    },
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
