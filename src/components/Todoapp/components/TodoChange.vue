<template>
  <div>
    <TodoButton :buttonName="MarkAll" />
    <TodoButton :buttonName="MarkAll" />
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
      MarkAll: "Mark All Completeds",
    };
  },
};
</script>
