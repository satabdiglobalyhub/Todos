<template>
  <div class="container">
    <h1 class="title">todos</h1>
    <div class="input">
      <TodoInput
        class="todo-input"
        :placeholder="placeholderText"
        v-model="todo"
        @newTodos="addNewTodo"
        @keyup.enter="addNewTodo"
        ref="todoInput"
      />
      <TodoButton
        class="todo-button"
        :buttonName="Submit"
        @click="addNewTodo"
      />
    </div>
    <div>
      <Todoslist :todos="todos" />
    </div>
    <div>
      buttons
    </div>
  </div>
</template>

<script>
import TodoInput from "../../UI/components/TodoInput.vue";
import Todoslist from "./components/Todoslist.vue";
import TodoButton from "../../UI/components/TodoButton.vue";

export default {
  components: {
    TodoInput,
    Todoslist,
    TodoButton,
  },
  data() {
    return {
      Submit: "Submit",
      placeholderText: "What needs to be done?",
      todo: "",
      todos: [],
    };
  },
  methods: {
    addNewTodo() {
      if (this.todo.length === 0) {
        return;
      } else {
        this.todos.push({
          id: Date.now(),
          done: false,
          content: this.todo,
        });

        this.$refs.todoInput.clearInput();
        this.todo = "";
      }
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
  border: 4px solid #2c3e50;
  border-radius: 5px;
}
.todo-input {
  width: 80%;
  padding: 10px 18px;
  font-size: 18px;
  border: none;
}
.todo-button {
  width: 20%;
  border-left: 4px solid #2c3e50;
  border-top: 0px;
  border-right: 0px;
  border-bottom: 0px;
  border-radius: 0px;
}
</style>
