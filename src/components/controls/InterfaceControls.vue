<template>
  <div class="interface-controls">
    <div class="control">
      <label>
        <input type="checkbox" v-model="enlargeCursor" @change="updateCursor" />
        Enlarge Cursor
      </label>
    </div>
    <div class="control"> 
      <label>
        <input type="checkbox" v-model="forceTooltips" @change="updateTooltips" />
        Force Visible Tooltips
      </label>
    </div>
    <div class="control">
      <label>
        <input type="checkbox" v-model="showHeadings" @change="updateHeadings" />
        Show Heading Outlines
      </label>
    </div>
  </div>
</template>

<script>
export default {
  name: "InterfaceControls",
  data() {
    return {
      enlargeCursor: JSON.parse(localStorage.getItem('enlargeCursor') || 'false'),
      forceTooltips: JSON.parse(localStorage.getItem('forceTooltips') || 'false'),
      showHeadings: JSON.parse(localStorage.getItem('showHeadings') || 'false')
    };
  },
  methods: {
    updateCursor() {
      if (this.enlargeCursor) {
        // Adjusted path to the cursor in the public folder
        document.body.style.cursor = "url('/cursors/large.cur'), auto";
      } else {
        document.body.style.cursor = "auto";
      }
      localStorage.setItem('enlargeCursor', this.enlargeCursor);
    },
    updateTooltips() {
      const elements = document.querySelectorAll('[title], [aria-label]');
      elements.forEach(el => {
        if (this.forceTooltips) {
          // Store tooltip content in data-tooltip and remove title/aria-label
          el.setAttribute("data-tooltip", el.title || el.getAttribute("aria-label"));
          el.removeAttribute("title");
          el.removeAttribute("aria-label");
        } else {
          // Restore title and aria-label attributes if tooltips are disabled
          el.removeAttribute("data-tooltip");
          el.setAttribute("title", el.getAttribute("data-tooltip"));
          el.setAttribute("aria-label", el.getAttribute("data-tooltip"));
        }
      });
      localStorage.setItem('forceTooltips', this.forceTooltips);
    },
    updateHeadings() {
      if (this.showHeadings) {
        const headings = document.querySelectorAll("h1, h2, h3, h4, h5, h6");
        headings.forEach(h => {
          h.style.borderBottom = "2px solid #FF0000"; // Adds red underline to all headings
        });
      } else {
        const headings = document.querySelectorAll("h1, h2, h3, h4, h5, h6");
        headings.forEach(h => {
          h.style.borderBottom = "none";
        });
      }
      localStorage.setItem('showHeadings', this.showHeadings);
    }
  }
};
</script>

<style scoped>
.interface-controls {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.control {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

/* CSS to force visible tooltips */
[data-tooltip]::after {
  content: attr(data-tooltip);
  position: absolute;
  top: -30px;
  left: 0;
  background-color: rgba(0, 0, 0, 0.75);
  color: #fff;
  padding: 5px;
  font-size: 0.9rem;
  border-radius: 4px;
  white-space: nowrap;
  visibility: visible; /* Always visible when checkbox is checked */
  opacity: 1;
  pointer-events: none; /* Ensure it does not interfere with other interactions */
}
</style>
