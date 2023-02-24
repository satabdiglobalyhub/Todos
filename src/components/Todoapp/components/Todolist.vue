<template>
  <div class="list">
    <ul >
      <li>static todolist <TodoButton :buttonName="Delete" /></li>
    </ul>
  </div>
</template>

<script>
import TodoButton from "../../../UI/components/TodoButton.vue";
export default {
  components: {
    TodoButton,
  },
  data() {
    return {
      Delete: "Delete",
    };
  },
};
</script>

<style>
.list {
  padding: 10px;
  border-bottom: 3px solid #2c3e50;
  font-size: xx-large;
  display: flex;
  margin: 0px 20px;
}
</style>
