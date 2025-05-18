# CSS3 Transitions, Animations, and Advanced JavaScript Functions

## Objectives

Create smooth CSS transitions and animations.
Use JavaScript functions for dynamic behavior.
Implement local storage for data persistence.

## Instructions
Add CSS animations to elements like buttons or images.

>[!NOTE]
> - Write a JavaScript function that:
> - Stores and retrieves user preferences using localStorage.
> - Implements an animation triggered by user actions.

## Tasks

Create a CSS animation.
Store data in localStorage.
Apply JavaScript to trigger animations.

index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Animated Theme Toggle</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>

  <div class="container">
    <h1>🎨 Animated Theme Toggle</h1>
    <button id="themeToggleBtn">Toggle Theme</button>
    <p id="statusMessage"></p>
  </div>

  <script src="script.js"></script>
</body>
</html>
style.css

body {
  font-family: 'Segoe UI', sans-serif;
  margin: 0;
  padding: 2em;
  background-color: white;
  color: black;
  transition: background-color 0.5s ease, color 0.5s ease;
}

body.dark-theme {
  background-color: #121212;
  color: white;
}

.container {
  text-align: center;
}

#themeToggleBtn {
  padding: 12px 24px;
  font-size: 1rem;
  border: none;
  border-radius: 5px;
  background-color: #6200ea;
  color: white;
  cursor: pointer;
  transition: transform 0.3s ease;
}

#themeToggleBtn.animate {
  animation: pulse 0.4s ease;
}

@keyframes pulse {
  0% { transform: scale(1); }
  50% { transform: scale(1.2); }
  100% { transform: scale(1); }
}
script.js
const themeToggleBtn = document.getElementById("themeToggleBtn");
const statusMessage = document.getElementById("statusMessage");

// Load theme preference on page load
window.addEventListener("DOMContentLoaded", () => {
  const savedTheme = localStorage.getItem("theme");
  if (savedTheme === "dark") {
    document.body.classList.add("dark-theme");
    statusMessage.textContent = "Dark theme loaded from your preferences.";
  } else {
    statusMessage.textContent = "Light theme loaded (default).";
  }
});

// Toggle theme and save to localStorage
themeToggleBtn.addEventListener("click", () => {
  document.body.classList.toggle("dark-theme");

  const currentTheme = document.body.classList.contains("dark-theme") ? "dark" : "light";
  localStorage.setItem("theme", currentTheme);
  statusMessage.textContent = `${currentTheme.charAt(0).toUpperCase() + currentTheme.slice(1)} theme saved!`;

  // Trigger CSS animation
  themeToggleBtn.classList.add("animate");

  // Remove animation class after it ends
  setTimeout(() => {
    themeToggleBtn.classList.remove("animate");
  }, 400);
});

Happy Coding! 💻✨
