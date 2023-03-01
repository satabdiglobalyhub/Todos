<template>
  <div class="container">
    <h1 class="title">todos</h1>
    <div class="input">
      <TodoInput
        class="todo-input"
        :placeholderText="'What needs to be done?'"
        v-model="todo"
        @newTodos="addNewTodo"
        @keyup.enter="addNewTodo"
        ref="todoInput"
      />
      <TodoButton
        class="todo-input-button"
        :buttonName="'Submit'"
        @click="addNewTodo"
      />
    </div>

    <div>
      <Todoslist :todos="todos" />
    </div>

    <div v-if="todos.length > 1" class="todo-buttons">
      <div class="todo-buttons-changes">
        <TodoButton
          :buttonName="'Mark All Completed'"
          @click="markAllCompleted"
        />
        <TodoButton :buttonName="'Delete All'" @click="deleteAll" />
        <TodoButton
          :buttonName="'Clear Completed'"
          @click="clearAllCompleted"
        />
      </div>
      <div class="todo-buttons-display">
        <TodoButton :buttonName="'Show All'" @click="showAll" />
        <TodoButton :buttonName="'Show Active'" @click="showActive" />
        <TodoButton :buttonName="'Show Completed'" @click="showCompleted" />
      </div>
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
      todo: "",
      todos: [],
      filteredTodos: [],
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
    markAllCompleted() {
      const allDone = this.todos.every((todos) => todos.done);
      this.todos.forEach((todos) => {
        todos.done = !allDone;
      });
    },
    deleteAll() {
      this.todos = [];
    },
    clearAllCompleted() {
      for (let i = this.todos.length - 1; i >= 0; i--) {
        if (this.todos[i].done == true) {
          this.todos.splice(i, 1);
        }
      }
    },
    showAll() {
      console.log("all", this.todos);
    },
    showActive() {
      const activeTodos = this.todos.filter((todo) => !todo.done);
      console.log("active", activeTodos);
    },
    showCompleted() {
      const completedTodos = this.todos.filter((todo) => todo.done);
      console.log("completed", completedTodos);
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
.todo-input-button {
  width: 22%;
  border-left: 4px solid #2c3e50;
  border-top: 0px;
  border-right: 0px;
  border-bottom: 0px;
  border-radius: 0px;
}
.todo-buttons {
  padding: 20px;
}
.todo-buttons-changes {
  display: flex;
  justify-content: space-between;
  color: #2c3e50;
  margin-bottom: 20px;
}
.todo-buttons-display {
  display: flex;
  justify-content: flex-start;
  gap: 10px;
}
</style>
