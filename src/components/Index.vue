<template>
  <TodoInput />
  <Todolist />
  <TodoButton />
</template>
<script>
import TodoInput from "../UI/components/TodoInput.vue";
import Todolist from "./Todoapp/components/Todolist.vue";
import TodoButton from "../UI/components/TodoButton.vue";
export default {
  components: {
    TodoInput,
    Todolist,
    TodoButton,
  },
};
</script>
<style></style>
