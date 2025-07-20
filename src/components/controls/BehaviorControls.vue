<template>
  <div class="behavior-controls">
    <div class="control">
      <label>
        <input type="checkbox" v-model="pauseAnimations" @change="updatePauseAnimations" />
        Pause Animations
      </label>
    </div>
    <div class="control">
      <label>
        <input type="checkbox" v-model="hideImages" @change="updateHideImages" />
        Hide Images
      </label>
    </div>
    <div class="control">
      <label>
        <input type="checkbox" v-model="dyslexiaFont" @change="updateDyslexiaFont" />
        Dyslexia-Friendly Font
      </label>
    </div>
  </div>
</template>

<script>
export default {
  name: "BehaviorControls",
  data() {
    return {
      pauseAnimations: JSON.parse(localStorage.getItem('pauseAnimations') || 'false'),
      hideImages: JSON.parse(localStorage.getItem('hideImages') || 'false'),
      dyslexiaFont: JSON.parse(localStorage.getItem('dyslexiaFont') || 'false'),
    };
  },
  methods: {
    updatePauseAnimations() {
      if (this.pauseAnimations) {
        // Add class to disable animations globally
        document.body.classList.add('no-animations');
      } else {
        // Remove class to enable animations again
        document.body.classList.remove('no-animations');
      }
      localStorage.setItem('pauseAnimations', this.pauseAnimations);
    },

    updateHideImages() {
      const images = document.querySelectorAll('img');
      images.forEach(img => {
        if (this.hideImages) {
          img.style.visibility = "hidden";
        } else {
          img.style.visibility = "visible";
        }
      });
      localStorage.setItem('hideImages', this.hideImages);
    },

    updateDyslexiaFont() {
      // Check if the dyslexia font link is already added to the head
      const existingLink = document.querySelector("link[href*='opendyslexic']");
      
      if (this.dyslexiaFont && !existingLink) {
        const link = document.createElement("link");
        link.href = "https://cdn.jsdelivr.net/npm/opendyslexic@latest/opendyslexic.css";
        link.rel = "stylesheet";
        document.head.appendChild(link);
      } else if (!this.dyslexiaFont && existingLink) {
        document.head.removeChild(existingLink);
      }

      localStorage.setItem('dyslexiaFont', this.dyslexiaFont);
    }
  }
};
</script>

<style scoped>
.behavior-controls {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.control {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
