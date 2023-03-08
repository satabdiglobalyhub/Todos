<template>
  <button @click="toggleButton" :class="buttonHoverColor">
    {{ buttonName }}
  </button>
</template>

<script>
export default {
  props: {
    buttonName: {
      type: String,
      default: "",
    },
    buttonHoverColor: {
      type: String,
      default: "",
    },
  },

  methods: {
    toggleButton() {
      this.$emit("handle-click");
      if (this.focusActive) {
        this.isActive = !this.isActive;
      }
    },
  },
};
</script>

<style>
button {
  font-size: 20px;
  border: 2px solid #2c3e50;
  border-radius: 5px;
  background-color: white;
  padding: 10px;
}
.green:hover {
  color: #2c3e50;
  background-color: #00ca4e;
}
.red:hover {
  color: #2c3e50;
  background-color: #ff605c;
}
.orange:hover{
  color:#2c3e50;
  background-color: #ffbd44;
}
.blue:hover{
color:#2c3e50;
background-color: #2a75ff;
}
button:hover {
  color: white;
  background-color: #2c3e50;
}
</style>
