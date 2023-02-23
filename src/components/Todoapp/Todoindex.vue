<template>
  <div>
    <Todoinput />
    <Todolist />
    <Todobutton />
  </div>
</template>

<script>
import Todoinput from "../../UI/components/TodoInput.vue";
import Todolist from "./components/Todolist.vue";
import Todobutton from "../../UI/components/TodoButton.vue";

export default {
  components: {
    Todoinput,
    Todolist,
    Todobutton,
  },
};
</script>

<style></style>
