<template>
  <input
    type="text"
    class="todo-input"
    :placeholder="placeholderText"
    v-model="inputValue"
    required
  />
</template>

<script>
export default {
  data() {
    return {
      inputValue: "",
    };
  },
  props: {
    placeholderText: {
      type: String,
      default: "Enter Todos",
    },
  },
  methods: {
    clearInput() {
      this.inputValue = "";
    },
  },
};
</script>

<style>
.form {
  display: flex;
  border: 3px solid #2c3e50;
}
.todo-input {
  padding: 10px 18px;
  font-size: 18px;
  border: none;
}
.todo-input:focus {
  outline: none;
}
</style>
