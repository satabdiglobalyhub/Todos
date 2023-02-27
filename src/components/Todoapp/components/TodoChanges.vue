<template>
  <div class="changes">
    <div class="changes-modify">
      <TodoButton :buttonName="MarkAll" />
      <TodoButton :buttonName="ClearCompleted" />
      <TodoButton :buttonName="DeleteAll" />
    </div>
    <div class="changes-display">
      <TodoButton :buttonName="ShowAll" />
      <TodoButton :buttonName="ShowActive" class="changes-display-showActive" />
      <TodoButton :buttonName="ShowCompleted" />
    </div>
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
      MarkAll: "Mark All Completed",
      ClearCompleted: "Clear Completed",
      DeleteAll: "Delete All",
      ShowAll: "Show All",
      ShowActive: "Show Active",
      ShowCompleted: "Show Completed",
    };
  },
};
</script>

<style>
.changes {
  margin: 20px 20px;
}
.changes-modify {
  display: flex;
  justify-content: space-between;
}
.changes-display {
  margin-top: 20px;
  display: flex;
}
.changes-display-showActive {
  margin: 0px 10px;
}
</style>
