<template>
  <div id="app">
    <TestPage />
    <FloatingButton @toggle-menu="toggleMenu" />
    <MenuPanel :isVisible="isMenuVisible" />
  </div>
</template>

<script>
import TestPage from './components/TestPage.vue';
import FloatingButton from './components/FloatingButton.vue';
import MenuPanel from './components/MenuPanel.vue';

export default {
  name: 'App',
  components: {
    TestPage,
    FloatingButton,
    MenuPanel
  },
  data() {
    return {
      isMenuVisible: false
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuVisible = !this.isMenuVisible;
    }
  }
};
</script>

<style>
/* Global Styles */
body {
  font-size: var(--font-size, 1rem);
}
</style>
