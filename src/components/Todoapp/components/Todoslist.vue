<template>
  <div v-if="reversedTodos.length" class="list">
    <div v-for="(todo, index) in reversedTodos" :key="index">
      <h3 :class="{ done: todo.done }" class="todo">
        <div class="todo-list">
          <input
            type="checkbox"
            :checked="todo.done"
            @click="todoCompleted(todo)"
            class="toggle"
          />
          <label :class="{ completed: todo.done }" @dblclick="editTodo(todo)">
            {{ todo.content }}
          </label>
        </div>
        <div>
          <TodoButton
            :buttonName="'Delete'"
            :buttonHoverColor="'red'"
            @Click="deleteTodo(todo.id)"
            class="todolist-button"
          />
        </div>
      </h3>
    </div>
  </div>
  <div v-else class="emptyList">
    <h2>Enter Todos</h2>
  </div>
</template>

<script>
import TodoButton from "../../../UI/components/TodoButton.vue";
import TodoInput from "../../../UI/components/TodoInput.vue";

export default {
  data() {
    return {
      displayTodos: [],
    };
  },
  components: {
    TodoButton,
    TodoInput,
  },
  props: {
    todos: {
      type: Array,
      dafault: [],
    },
  },
  methods: {
    saveTodos() {
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
    todoCompleted(todo) {
      todo.done = !todo.done;
      this.saveTodos();
    },
    editTodo(todo) {
      const newContent = prompt("Enter new content", todo.content);
      if (newContent !== null && newContent !== "") {
        todo.content = newContent;
        this.saveTodos();
      }
    },
    deleteTodo(id) {
      const index = this.todos.findIndex((todo) => todo.id === id);
      if (index !== -1) {
        this.todos.splice(index, 1);
        this.saveTodos();
      }
    },
  },
  computed: {
    reversedTodos() {
      return this.todos.slice().reverse();
    },
  },
  mounted() {
    this.displayTodos = JSON.parse(localStorage.getItem("todos"));
  },
};
</script>

<style>
h3 {
  margin: 25px;
}
.list {
  /* padding: 0px 10px; */
  border-bottom: 3px solid #2c3e50;
  font-size: x-large;
  display: flex;
  flex-direction: column;
  overflow: scroll;
  max-height: 50vh;
  scrollbar-width: thin;
  scrollbar-color: #2c3e50;
}
.emptyList {
  padding: 0px 20px;
  border-bottom: 3px solid #2c3e50;
  font-size: xx-large;
  display: flex;
  justify-content: center;
  margin: 30px 0px;
}
.todo {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  overflow: scroll;
}
.todo-list {
  display: flex;
  align-items: flex-start;
}
.toggle {
  margin-right: 15px;
}
.todo-list input {
  margin-top: 15px;
}
.todo-list label {
  display: flex;
  flex-wrap: wrap;
  max-width: 385px;
  margin-right: 15px;
  cursor: pointer;
  word-break: break-all;
  padding: 5px;
}
.completed {
  color: #949494;
  text-decoration: line-through;
}
.emptyList {
  color: #2c3e50;
}
.todolist-button {
  display: flex;
  justify-content: flex-end;
}

.list::-webkit-scrollbar {
  height: 8px;
}

.list::-webkit-scrollbar-thumb {
  background-color: #2c3e50;
  border-radius: 12px;
}
.toggle {
  cursor: pointer;
}
</style>
