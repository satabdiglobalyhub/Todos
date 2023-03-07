<template>
  <button @click="toggleButton" :class="{ active: isActive }">
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
    focusActive: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      isActive: false,
    };
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
button:hover {
  color: white;
  background-color: #2c3e50;
}
.active {
  color: white;
  background-color: #2c3e50;
}
</style>
