<template>
  <div v-if="todos.length" class="list">
    <div v-for="(todo, index) in todos" :key="index">
      <h3 :class="{ done: todo.done }" class="todo">
        <div>
          <input
            type="checkbox"
            
            :checked="todo.done"
            @click="todoCompleted(todo)"
          />
          <label :class="{ completed: todo.done }" @dblclick="editTodo(todo)">
            {{ todo.content }}
          </label>
        </div>
        <div>
          <TodoButton
            :buttonName="'Delete'"
            @Click="deleteTodo(index)"
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
    deleteTodo(index) {
      this.todos.splice(index, 1);
      this.saveTodos();
    },
  },
};
</script>

<style>
h3 {
  margin: 25px;
}
.list {
  padding: 0px 10px;
  border-bottom: 3px solid #2c3e50;
  font-size: xx-large;
  display: flex;
  flex-direction: column;
  overflow: scroll;
  height: 50vh;
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
  align-items: baseline;
}
.todo input,
.todo label {
  margin-right: 15px;
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
</style>
