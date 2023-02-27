<template>
  <div class="container">
    <h1 class="title">todos</h1>
    <div class="input">
      <TodoInput
        class="todo-input"
        :placeholder="placeholderText"
        @newTodos="addNewTodo"
      />
      <TodoButton class="todo-button" :buttonName="Submit" />
    </div>

    <div class="todo-list">
      <TodoList :TodoList="todos" />{{ this.todos }}
    </div>
  </div>
</template>

<script>
import TodoInput from "../../UI/components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";
import TodoButton from "../../UI/components/TodoButton.vue";

export default {
  components: {
    TodoInput,
    TodoList,
    TodoButton,
  },
  data() {
    return {
      Submit: "Submit",
      placeholderText: "What needs to be done?",
      newTodo: "",
      todos: [],
    };
  },
  methods: {
    addNewTodo(newItem) {
      this.todos = {
        id: Date.now(),
        done: false,
        content: newItem,
      };
      console.log(this.todos);
    },
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
