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

TODO: Vue.js Router

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
      /* employees: [
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
      ], */
      // empty array for async API
      employees: [],
    };
  },

  // lifecycle method
  mounted() {
    this.getEmployees();
  },

  /* example of async fetch API
  async asynchronousMethod() {
    try {
      const response = await fetch('url')
      const data = await response.json()

      // do something with `data`
    } catch (error) {
      // do something with `error`
    }
  } */

  methods: {
    /* CRUD methods
    create
    addEmployee(employee) {
      this.employees = [...this.employees, employee]
      const lastId =
        this.employees.length > 0
          ? this.employees[this.employees.length - 1].id
          : 0;
      const id = lastId + 1;
      const newEmployee = { ...employee, id };

      this.employees = [...this.employees, newEmployee];
    },

    delete
    deleteEmployee(id) {
      this.employees = this.employees.filter((employee) => employee.id !== id);
    },

    update
    editEmployee(id, updatedEmployee) {
      this.employees = this.employees.map((employee) =>
        employee.id === id ? updatedEmployee : employee
      );
    }, */

    // async fetch API methods

    // GET
    async getEmployees() {
      try {
        const respones = await fetch(
          "https://jsonplaceholder.typicode.com/users"
        );
        const data = await respones.json();
        this.employees = data;
      } catch (error) {
        console.error(error);
      }
    },

    // POST
    async addEmployee(employee) {
      try {
        const respones = await fetch(
          "https://jsonplaceholder.typicode.com/users",
          {
            method: "POST",
            body: JSON.stringify(employee),
            headers: { "Content-type": "application/json; charset=UTF-8" },
          }
        );

        const data = await respones.json();
        this.employees = [...this.employees, data];
      } catch (error) {
        console.error(error);
      }
    },

    // PUT
    async editEmployee(id, updatedEmployee) {
      try {
        const response = await fetch(
          `https://jsonplaceholder.typicode.com/users/${id}`,
          {
            method: "PUT",
            body: JSON.stringify(updatedEmployee),
            headers: { "Content-type": "application/json; cahrset=UTF-8" },
          }
        );
        const data = response.json();
        this.employees = this.employees.map((employee) =>
          employee.id === id ? data : employee
        );
      } catch (error) {
        console.error(error);
      }
    }, // * when employee is updated and saved all data in row is deleted

    // DELETE
    async deleteEmployee(id) {
      try {
        await fetch(`https://jsonplaceholder.typicode.com/users/${id}`, {
          method: "DELETE",
        });
        this.employees = this.employees.filter(
          (employee) => employee.id !== id
        );
      } catch (error) {
        console.error(error);
      }
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
