<template>
  <div class="visual-controls">
    <div class="control">
      <label>
        <input type="checkbox" v-model="contrast" @change="updateContrast" />
        High Contrast
      </label>
    </div>
    <div class="control">
      <label>
        <input type="checkbox" v-model="highlightLinks" @change="updateHighlightLinks" />
        Highlight Links
      </label>
    </div>
    <div class="control">
      <label>
        Bigger Text
        <input type="range" v-model="fontSize" min="1" max="2" step="0.1" @input="updateFontSize" />
      </label>
    </div>
    <div class="control">
      Text Spacing
      <input type="range" v-model="textSpacing" min="0" max="2" step="0.1" @input="updateTextSpacing" />
    </div>
  </div>
</template>

<script>
export default {
  name: "VisualControls",
  data() {
    return {
      contrast: JSON.parse(localStorage.getItem('contrast') || 'false'),
      highlightLinks: JSON.parse(localStorage.getItem('highlightLinks') || 'false'),
      fontSize: parseFloat(localStorage.getItem('fontSize') || '1'),
      textSpacing: parseFloat(localStorage.getItem('textSpacing') || '0')
    };
  },
  methods: {
    updateContrast() {
      if (this.contrast) {
        document.documentElement.style.filter = "contrast(120%)";
      } else {
        document.documentElement.style.filter = "contrast(100%)";
      }
      localStorage.setItem('contrast', this.contrast);
    },
    updateHighlightLinks() {
      const links = document.querySelectorAll('a');
      links.forEach(link => {
        if (this.highlightLinks) {
          link.style.borderBottom = "2px solid red";
        } else {
          link.style.borderBottom = "none";
        }
      });
      localStorage.setItem('highlightLinks', this.highlightLinks);
    },
    updateFontSize() {
      // Update font size dynamically using a custom CSS variable
      document.documentElement.style.setProperty("--font-size", `${this.fontSize}rem`);
      localStorage.setItem('fontSize', this.fontSize);
    },
    updateTextSpacing() {
      // Update text spacing dynamically using custom CSS variables
      document.documentElement.style.setProperty("--text-spacing", `${this.textSpacing}rem`);
      localStorage.setItem('textSpacing', this.textSpacing);
    }
  }
};
</script>

<style scoped>
.visual-controls {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.control {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

input[type="range"] {
  width: 150px;
}

</style>
