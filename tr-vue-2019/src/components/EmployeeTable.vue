<template>
  <div id="emplyee-table">
    <table>
      <thead>
        <tr>
          <th>Employee name</th>
          <th>Employee email</th>
        </tr>
      </thead>
      <tbody>
        <tr>
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
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "employee-table",
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
