# A11y Widget Project

## Overview

The A11y Widget is a comprehensive accessibility tool that enables users to customize their browsing experience for better accessibility. The widget allows users to adjust visual settings, pause animations, hide images, and more to improve web accessibility. This project is built with **Vue.js** and utilizes **localStorage** for persisting settings across page reloads.

## Features

- **Contrast+**: Adjust the color contrast for better readability.
- **Text Size**: Increase or decrease the font size for better legibility.
- **Dyslexia-Friendly Font**: Switch to OpenDyslexic font for better reading experience.
- **Pause Animations**: Pause all animations on the webpage for users who may have motion sensitivity.
- **Hide Images**: Hide all images for a more focused experience.
- **Enlarge Cursor**: Enlarge the cursor for better visibility.
- **Force Tooltips**: Force visible alt-text on hover.
- **Show Heading Outlines**: Highlight heading outlines to improve content navigation.

## Setup Instructions

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Rohit-Kushwaha-483/a11y-widget.git
    ```

2. **Navigate into the project directory** :
   ```bash
   cd a11y-widget
    ```
3. **Install dependencies** :
    ```bash
    npm install
    ```
4. **Run the development server** :
    ```bash
    npm run dev
    ```

5. **Open the project in your browser** :

    Visit http://localhost:5173/ to view the widget in action.

## Implementation Choices
- Vue.js: Chose Vue.js for its simplicity and reactivity, making it an ideal framework for managing dynamic UI states like accessibility settings.

- localStorage: Utilized localStorage to persist user preferences across page reloads. This ensures that accessibility settings remain consistent for users during their browsing session.

- Dyslexia-Friendly Font: Integrated the OpenDyslexic font via a CDN to provide a dyslexia-friendly reading experience for users.

- Custom Cursor: Added the ability to enlarge the cursor for users with visual impairments.

- Behavior Controls: Implemented features to pause animations, hide images, and provide visible tooltips to enhance accessibility.

<!-- **Demo Video** : 

You can view the demo of the widget here: -->