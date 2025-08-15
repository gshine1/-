<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>G-Shine Hardware</title>
<style>
:root {
  --bg: #f4f4f4;
  --text: #222;
  --accent: #2196f3;
  --input-bg: #fff;
  --cart-bg: #fff;
  --cart-text: #222;
}

body {
  background: var(--bg);
  color: var(--text);
  font-family: Arial, sans-serif;
  margin: 0;
  transition: background 0.4s, color 0.4s;
}

header {
  background: var(--accent);
  color: white;
  padding: 1rem;
  text-align: center;
  transition: background 0.4s;
}

.theme-switcher {
  margin: 1rem;
  text-align: center;
}

.theme-switcher button {
  background: none;
  border: 1px solid var(--accent);
  color: var(--text);
  padding: 0.5rem 1rem;
  margin: 0 0.3rem;
  cursor: pointer;
  border-radius: 5px;
  transition: all 0.3s;
}

.theme-switcher button.active {
  background: var(--accent);
  color: white;
}

.product-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 1rem;
  padding: 1rem;
}

.product {
  background: var(--cart-bg);
  color: var(--cart-text);
  border-radius: 10px;
  overflow: hidden;
  border: 1px solid #ddd;
  text-align: center;
  transition: all 0.4s ease;
}

.product img {
  width: 100%;
  transition: transform 0.4s, box-shadow 0.4s;
}

.product:hover img {
  transform: scale(1.05);
}

.product h3 {
  margin: 0.5rem 0;
}

.product p {
  font-size: 0.9rem;
  margin: 0.5rem;
}

/* Dark Theme */
body.dark {
  --bg: #1e1e1e;
  --text: #ddd;
  --accent: #ff9800;
  --input-bg: #2a2a2a;
  --cart-bg: #2a2a2a;
  --cart-text: #ddd;
}

body.dark .product {
  border: 1px solid #444;
}

/* Royal Gold Theme */
body.royal {
  --bg: #1a1a1a;
  --text: #f9eac3;
  --accent: #d4af37;
  --input-bg: #2a2a2a;
  --cart-bg: #242424;
  --cart-text: #f9eac3;
}

body.royal header {
  background: linear-gradient(135deg, #2b2b2b, #1a1a1a);
  border-bottom: 3px solid var(--accent);
}

body.royal .product {
  border: 1px solid var(--accent);
  box-shadow: 0 0 10px rgba(212, 175, 55, 0.4);
  animation: goldGlow 2s infinite alternate;
}

body.royal .theme-switcher button {
  border: 1px solid var(--accent);
}

body.royal .theme-switcher button.active {
  background: var(--accent);
  color: #222;
}

/* Glowing Animation for Royal Gold */
@keyframes goldGlow {
  from {
    box-shadow: 0 0 10px rgba(212, 175, 55, 0.4);
  }
  to {
    box-shadow: 0 0 20px rgba(212, 175, 55, 0.8);
  }
}
</style>
</head>
<body>

<header>
  <h1>G-Shine Hardware</h1>
</header>

<div class="theme-switcher">
  <span>Theme:</span>
  <button id="theme-light" onclick="setTheme('light')">Light</button>
  <button id="theme-dark" onclick="setTheme('dark')">Dark</button>
  <button id="theme-royal" onclick="setTheme('royal')">Royal Gold</button>
</div>

<div class="product-list">
  <div class="product">
    <img src="https://via.placeholder.com/200x150" alt="Product 1">
    <h3>Waste Pipe 4" (GB) Heavy</h3>
    <p>KSh 1,200</p>
  </div>
  <div class="product">
    <img src="https://via.placeholder.com/200x150" alt="Product 2">
    <h3>Steel Rod 12mm</h3>
    <p>KSh 750</p>
  </div>
  <div class="product">
    <img src="https://via.placeholder.com/200x150" alt="Product 3">
    <h3>Water Tap Brass</h3>
    <p>KSh 450</p>
  </div>
</div>

<script>
function setTheme(theme) {
  document.body.classList.remove('dark', 'royal');
  if (theme === 'dark') {
    document.body.classList.add('dark');
  } else if (theme === 'royal') {
    document.body.classList.add('royal');
  }
  document.querySelectorAll('.theme-switcher button').forEach(btn => btn.classList.remove('active'));
  document.getElementById('theme-' + theme).classList.add('active');
  localStorage.setItem('theme', theme);
}

// Load saved theme
const savedTheme = localStorage.getItem('theme') || 'light';
setTheme(savedTheme);
</script>

</body>
</html>
