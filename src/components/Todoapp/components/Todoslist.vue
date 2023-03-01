<template>
  <div v-if="todos.length" class="list">
    <div v-for="(todo, index) in todos" :key="index">
      <h3 :class="{ done: todo.done }" class="todo">
        <input
          type="checkbox"
          :checked="todo.done"
          @click="todoCompleted(todo)"
        />
        <label :class="{ completed: todo.done }" @dblclick="editTodo(todo)">
          {{ todo.content }}
        </label>
        <TodoButton :buttonName="Delete" @Click="deleteTodo(index)" />
      </h3>
    </div>
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
  data() {
    return {
      Delete: "Delete",
    };
  },
  methods: {
    todoCompleted(todo) {
      todo.done = !todo.done;
    },
    editTodo(todo) {
      const newContent = prompt("Enter new content", todo.content);
      if (newContent !== null && newContent !== "") {
        todo.content = newContent;
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style>
.list {
  padding: 10px;
  border-bottom: 3px solid #2c3e50;
  font-size: xx-large;
  display: flex;
  flex-direction: column;
  margin: 0px 20px;
}
.todo {
  display: flex;
  justify-content: flex-start;
}
.todo input,
.todo label {
  margin-right: 15px;
}
.completed {
  color: #2c3e50;
  text-decoration: line-through;
}
</style>
