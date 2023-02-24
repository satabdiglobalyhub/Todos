<template>
  <div class="container">
    <h1 class="title">todos</h1>
    <div class="input">
      <TodoInput class="todo-input" />
      <TodoButton class="todo-button" :buttonName="Submit" />
    </div>
    <div>
      <TodoList />
      <!-- did not add Todobutton here to add it in the Todolist  -->
    </div>
    <div>
      <TodoChange />
    </div>
  </div>
</template>

<script>
import TodoInput from "../../UI/components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";
import TodoButton from "../../UI/components/TodoButton.vue";
import TodoChange from "./components/Todochange.vue";

export default {
  components: {
    TodoInput,
    TodoList,
    TodoButton,
    TodoChange,
  },
  data() {
    return {
      Submit: "Submit",
    };
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
#app {
  font-family: Arial, Helvetica, sans-serif;
  color: #2c3e50;
  margin-top: 60px;
  font-size: 24px;
}
.container {
  max-width: 600px;
  margin: 0 auto;
}
.title {
  margin-top: 50px;
  display: flex;
  justify-content: center;
}
.input {
  display: flex;
  width: 100%;
  border: 3px solid #2c3e50;
  border-radius: 8px;
}
.todo-input {
  width: 80%;
  padding: 10px 18px;
  font-size: 18px;
  border: none;
}
.todo-button {
  width: 20%;
  border-left: 3px solid #2c3e50;
  border-top: 0px;
  border-right: 0px;
  border-bottom: 0px;
}
</style>
