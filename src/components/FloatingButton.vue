<template>
    <div class="floating-button" @click="toggleMenu">
      <button class="btn">
        <span>🔧</span> <!-- A simple wrench icon -->
      </button>
    </div>
  </template>
  
  <script>
  export default {
    name: "FloatingButton",
    methods: {
      toggleMenu() {
        // Emit event to toggle the accessibility menu
        this.$emit('toggle-menu');
      }
    }
  };
  </script>
  
  <style scoped>
  .floating-button {
    position: fixed;
    bottom: 20px;
    right: 20px;
    z-index: 1000;
  }
  
  .btn {
    padding: 10px 15px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 50%;
    cursor: pointer;
  }
  
  .btn span {
    font-size: 20px;
  }
  </style>
  