<template>
  <div id="employee-form">
    <form @submit.prevent="handleSubmit">
      <label>Employee Name</label>
      <input
        type="text"
        v-model="employee.name"
        :class="{ 'has-error': submitting && invalidName }"
        @focus="clearStatus"
        @keypress="clearStatus"
      />
      <label>Empolyee Email</label>
      <input
        type="text"
        v-model="employee.email"
        :class="{ 'has-error': submitting && invalidEmail }"
        @focus="clearStatus"
      />
      <p v-if="error && submitting" class="error-message">
        Please fill out all required fields
      </p>
      <p v-if="success" class="success-message">Employee successfully added</p>
      <button v-on:click.prevent="handleSubmit">Add Empolyee</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "emloyee-form",
  // data f-n
  data() {
    return {
      // submitting state to check form submiting
      submitting: false,
      // error state
      error: false,
      // success state
      success: false,
      employee: {
        name: "",
        email: "",
      },
    };
  },
  // methods obj
  methods: {
    // add new employee
    handleSubmit() {
      //console.log("teseting handleSubmit");

      this.submitting = true;
      this.clearStatus();

      if (this.invalidName || this.invalidEmail) {
        this.error = true;
        return;
      }

      this.$emit("add:employee", this.employee);

      this.employee = {
        name: "",
        email: "",
      };

      this.error = false;
      this.success = true;
      this.submitting = false;
    },

    clearStatus() {
      this.success = false;
      this.error = false;
    },
  },
  // computed obj
  computed: {
    invalidName() {
      return this.employee.name === "";
    },

    invalidEmail() {
      return this.employee.email === "";
    },
  },
};
</script>

<style scoped>
form {
  margin-bottom: 2rem;
}

[class*="-message"] {
  font-weight: 500;
}

.error-message {
  color: #d33c40;
}

.success-message {
  color: #32a95d;
}
</style>
