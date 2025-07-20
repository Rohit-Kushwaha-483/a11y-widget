<template>
  <div v-if="isVisible" class="menu-panel">
    <!-- Visual Controls Section -->
    <VisualControls />
    
    <!-- Behavior Controls Section -->
    <BehaviorControls />
    
    <!-- Interface Controls Section -->
    <InterfaceControls />
  </div>
</template>

<script>
// Import all the controls
import VisualControls from './controls/VisualControls.vue';
import BehaviorControls from './controls/BehaviorControls.vue';
import InterfaceControls from './controls/InterfaceControls.vue';

export default {
  name: "MenuPanel",
  props: {
    isVisible: Boolean
  },
  components: {
    VisualControls,
    BehaviorControls,
    InterfaceControls
  },
  data() {
    return {
      settings: {
        contrast: false,
        largeText: false,
        dyslexiaFont: false,
        pauseAnimations: false,
        hideImages: false,
        enlargeCursor: false,
        forceTooltips: false,
        showHeadings: false
      }
    };
  },
  methods: {
    // Sync settings to localStorage and apply changes dynamically
    updateSettings() {
      localStorage.setItem('settings', JSON.stringify(this.settings));
    }
  },
  watch: {
    isVisible(newVal) {
      if (newVal) {
        const savedSettings = JSON.parse(localStorage.getItem('settings')) || this.settings;
        this.settings = { ...this.settings, ...savedSettings };
      }
    }
  }
};
</script>

<style scoped>
.menu-panel {
  position: fixed;
  bottom: 70px;
  right: 20px;
  background-color: #000000;
  padding: 20px;
  border: 1px solid white;

  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  border-radius: 8px;
  z-index: 1000;
}

.controls {
  display: flex;
  flex-direction: column;
}

.control {
  margin: 10px 0;
  color: #f0f0f0;
}

label {
  font-size: var(--font-size, 1rem);
}

input[type="checkbox"] {
  margin-right: 10px;
}
</style>