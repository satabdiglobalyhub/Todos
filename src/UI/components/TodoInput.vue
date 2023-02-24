<template>
  <input
    type="text"
    placeholder="What needs to be done?"
    class="todo-input"
    required
  />
</template>

<script></script>

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
