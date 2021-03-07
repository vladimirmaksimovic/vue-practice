<template>
  <div id="employee-form">
    <form action="">
      <label for="">Employee Name</label>
      <input v-model="employee.name" type="text" />
      <label for="">Empolyee Email</label>
      <input v-model="employee.email" type="text" />
      <button v-on:click.prevent="handleSubmit">Add Empolyee</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "emloyee-form",
  data() {
    return {
      employee: {
        name: "",
        email: "",
      },
    };
  },
  methods: {
    // add new employee
    handleSubmit() {
      //console.log("teseting handleSubmit");
      this.$emit("add:employee", this.employee);
    },
  },
};
</script>

<style scoped>
form {
  margin-bottom: 2rem;
}
</style>
