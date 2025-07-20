<template>
    <div class="test-page">
      <h1>This is a Main Heading (h1)</h1>
      <h2>This is a Subheading (h2)</h2>
      <h3>This is a Sub-subheading (h3)</h3>
      <h4>This is a Smaller Heading (h4)</h4>
      <h5>This is an Even Smaller Heading (h5)</h5>
      <h6>This is the Smallest Heading (h6)</h6>
  
      <p class="content">
        This is a sample paragraph of text that will be useful for testing the "Bigger Text" feature. You can increase the text size to make it more readable.
      </p>
      <p class="content">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
      </p>
  
      <div class="highlight-links">
        <p>Here are some <a href="#">hyperlinks</a> that you can test. Hover over them to see how they behave when highlighted.</p>
        <p>Check out these <a href="#">other links</a> to verify the highlighting feature.</p>
      </div>
  
      <div>
        <h3>Sample Images</h3>
        <img src="../assets/1.png" alt="Placeholder Image" width="300">      
        <img src="../assets/2.png" alt="Placeholder Image" width="300">      
        <img src="../assets/3.png" alt="Placeholder Image" width="300">      
      </div>
  
      <div class="animate-text">
        <p>This text is bouncing due to the animation. Test the "Pause Animations" feature to see if it stops.</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "TestPage"
  };
  </script>
  
  <style scoped>
  .test-page {
    font-family: Arial, sans-serif;
    padding: 20px;
  }
  .highlight-links a {
    text-decoration: none;
    color: #3498db;
    transition: color 0.3s ease;
  }
  .highlight-links a:hover {
    color: #e74c3c;
  }
  .animate-text {
    animation: bounce 2s infinite;
  }
  @keyframes bounce {
    0% { transform: translateY(0); }
    50% { transform: translateY(-10px); }
    100% { transform: translateY(0); }
  }
  </style>
  