<template>
  <div id="employee-table">
    <p v-if="employees.length < 1" class="empty-table">No employees</p>
    <table>
      <thead>
        <tr>
          <th>Employee name</th>
          <th>Employee email</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <!-- v-for / :key - loop through data and display -->
        <tr v-for="employee in employees" :key="employee.id">
          <td>{{ employee.name }}</td>
          <td>{{ employee.email }}</td>
          <td>
            <button>Edit</button>
            <button @click="$emit('delete:employee', employee.id)">
              Delete
            </button>
          </td>
        </tr>
        <!-- <tr>
          <td>Mile Prpic</td>
          <td>prpa@mail.com</td>
        </tr>
        <tr>
          <td>Jeca Peca</td>
          <td>ecapeca@mail.com</td>
        </tr>
        <tr>
          <td>Djole Mara</td>
          <td>djara@mail.com</td>
        </tr> -->
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "employee-table",
  // catch props from parent component
  props: {
    employees: Array,
  },
};
</script>

<style scoped>
thead {
  background: #009435;
  color: #f1f1f1;
}

tr:hover {
  background: #aae778;
  /* color: #f1f1f1 */
}

button {
  margin: 0 0.5rem 0 0;
}
</style>
