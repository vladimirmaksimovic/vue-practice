<template>
  <div id="employee-table">
    <table>
      <thead>
        <tr>
          <th>Employee name</th>
          <th>Employee email</th>
        </tr>
      </thead>
      <tbody>
        <!-- v-for / :key - loop through data and display -->
        <tr v-for="employee in employees" :key="employee.id">
          <td>{{ employee.name }}</td>
          <td>{{ employee.email }}</td>
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
  background: #009435;
  color: #f1f1f1;
}
</style>
