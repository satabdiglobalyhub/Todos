<template>
  <button>{{ buttonName }}</button>
</template>

<script>
export default {
  props: {
    buttonName: {
      type: String,
      default: "",
    },
  },
};
</script>

<style>
button {
  font-size: 20px;
  border: 1px solid #2c3e50;
  border-radius: 5px;
  background-color: white;
}
button:hover {
  color: white;
  background-color: #2c3e50;
}
</style>
