<template>
  <div class="container">
    <h1 class="title">todos</h1>
    <form @submit.prevent="addNewTodo" class="input">
      <TodoInput
        class="todo-input"
        :placeholder="placeholderText"
        :required="isrequired"
        name="newTodo"
        v-model="newTodo"
      />
      <TodoButton class="todo-button" :buttonName="Submit" />
    </form>

    <div class="todo-list">
      <TodoList />
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
      isrequired: true,
      newTodo: "",
      todos: {},
    };
  },
  methods: {
    addNewTodo() {
      this.todos = {
        id: Date.now(),
        done: false,
        content: this.newTodo,
      };
      this.newTodo = "";
      this.saveData();
      this.$emit("updatedTodoList");
    },
    saveData() {
      let todosLists = JSON.parse(localStorage.getItem("todos")) || [];
      todosLists.push(this.todos);
      localStorage.setItem("todos", JSON.stringify(todosLists));
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
