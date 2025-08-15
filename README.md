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
  font-family: Arial, sans-serif; margin: 0; background: var(--bg); color: var(--text);
  transition: background 0.3s, color 0.3s;
}
header {background: #333; color: white; text-align: center; padding: 0;}
header img {max-width: 100%; height: auto; display: block; margin: 0 auto;}
h1 {margin: 0; font-size: 2rem; padding: 0.5rem;}
.tagline {font-size: 1rem; font-style: italic; margin-bottom: 1rem;}
.search-container {
  position: sticky;
  top: 0;
  z-index: 100;
  background: var(--input-bg);
  text-align: center;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
  padding: 1rem 0 0.5rem 0;
}
.search-container input {
  width: 80%;
  padding: 0.5rem;
  font-size: 1rem;
  border: 1px solid #bbb;
  border-radius: 6px;
  background: var(--input-bg);
  color: var(--text);
  transition: background 0.3s, color 0.3s;
}
.search-suggestions {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 80%;
  background: var(--input-bg);
  border: 1px solid #bbb;
  border-radius: 6px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.08);
  max-height: 180px;
  overflow-y: auto;
  text-align: left;
  margin-top: 2px;
  z-index: 9999;
  display: none;
  color: var(--text);
}
.search-suggestions li {
  padding: 8px 12px;
  cursor: pointer;
  border-bottom: 1px solid #f0f0f0;
  background: var(--input-bg);
}
.search-suggestions li:last-child {border-bottom: none;}
.search-suggestions li:hover {background: #f5faff;}
.category-filter-container {
  width: 100%;
  text-align: center;
  margin: 1em 0 0.5em 0;
}
.category-filter {
  display: inline-block;
  margin: 0 5px;
  background: var(--accent);
  color: #fff;
  border: none;
  border-radius: 20px;
  padding: 0.4em 1em;
  font-size: 1em;
  cursor: pointer;
  transition: background 0.2s;
}
.category-filter.active,
.category-filter:hover {
  background: #1976d2;
}
.product-list-container {
  padding: 1.5em 0 5em 0;
}
.products {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
  justify-content: center;
  margin-top: 1em;
}
.product {
  width: 360px;
  background: var(--cart-bg);
  color: var(--cart-text);
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.08);
  border: 1px solid #ddd;
  padding: 1em;
  text-align: center;
  transition: background 0.3s, color 0.3s;
  position: relative;
}
.product img {
  width: 100%;
  height: 260px;
  object-fit: contain;
  margin-bottom: 1em;
  border-radius: 6px;
  box-shadow: 0 1px 4px rgba(0,0,0,0.06);
  cursor: pointer;
  transition: box-shadow 0.2s;
}
.product img:hover {
  box-shadow: 0 0 8px #2196f3;
}
.product .price {
  color: green;
  font-weight: bold;
  margin: 0.5em 0;
}
.product .cart {
  background: var(--accent);
  color: #fff;
  border: none;
  padding: 0.5em 1em;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 0.5em;
}
.product .cart:hover {background: #1976d2;}
.highlight {background: yellow;}
#whatsapp-float {position: fixed; bottom: 80px; right: 20px; width: 55px; height: 55px; background: #25d366; border-radius: 50%; display: flex; align-items: center; justify-content: center; box-shadow: 0 2px 6px rgba(0,0,0,0.3); cursor: pointer; z-index: 10000;}
#whatsapp-float img {width: 30px; height: 30px;}
#floating-cart {
  position: fixed;
  bottom: 60px;
  left: 20px;
  background: var(--accent);
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 25px;
  cursor: pointer;
  z-index: 10000;
  box-shadow: 0 2px 8px rgba(0,0,0,0.3);
  font-size: 1rem;
  display: flex;
  align-items: center;
  gap: 6px;
}
#cart-panel {
  position: fixed;
  bottom: 120px;
  left: 20px;
  background: var(--cart-bg);
  color: var(--cart-text);
  border: 1px solid #ccc;
  border-radius: 8px;
  width: 280px;
  max-height: 400px;
  overflow-y: auto;
  box-shadow: 0 2px 12px rgba(0,0,0,0.3);
  padding: 1rem;
  display: none;
  z-index: 10000;
  transition: background 0.3s, color 0.3s;
}
#cart-panel h4 {margin-top: 0;}
#cart-panel ul {list-style: none; padding: 0; margin: 0 0 0.5rem 0;}
#cart-panel li {
  border-bottom: 1px solid #eee;
  padding: 8px 0;
  font-size: 0.9rem;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}
.cart-controls {
  display: flex;
  gap: 4px;
  margin-top: 4px;
}
.cart-controls button {
  padding: 2px 6px;
  font-size: 0.8rem;
  border: none;
  background: #ddd;
  border-radius: 4px;
  cursor: pointer;
}
.cart-controls button:hover {background: #bbb;}
#cart-panel p {font-weight: bold; margin: 0.5rem 0;}
#cart-panel button {
  background: #4caf50;
  color: white;
  border: none;
  padding: 0.5rem;
  border-radius: 5px;
  cursor: pointer;
  width: 100%;
}
#cart-panel button:hover {background: #388e3c;}
.theme-switcher {
  position: fixed;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  background: var(--cart-bg);
  color: var(--cart-text);
  border: 1px solid #ccc;
  border-radius: 30px;
  box-shadow: 0 2px 12px rgba(0,0,0,0.04);
  padding: 0.5em 1em;
  z-index: 10001;
  font-size: 1em;
  display: flex;
  gap: 10px;
  align-items: center;
  transition: background 0.3s, color 0.3s;
}
.theme-switcher button {
  background: var(--accent);
  color: #fff;
  border: none;
  padding: 0.3em 1em;
  border-radius: 20px;
  font-size: 1em;
  cursor: pointer;
  margin: 0 2px;
}
.theme-switcher button.active {
  background: #222;
}
//* Keep images contained inside product cards */
.product {
  position: relative;
  overflow: hidden; /* Prevents zoom/bounce from spilling out */
}

/* Keep images contained inside product cards */
.product {
  position: relative;
  overflow: hidden; /* Prevents zoom/bounce from spilling out */
}

/* Product Image Animations */
.product img {
  opacity: 0;
  transform: scale(0.97);
  animation: fadeInScale 0.5s ease forwards;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  width: 100%;
  display: block;
  object-fit: cover;
}

.product img:hover {
  animation: bounceSoft 0.5s ease;
  transform: scale(1.03) translateY(-3px);
  box-shadow: 0 6px 12px rgba(0,0,0,0.12);
}

/* Fade-in & scale on load */
@keyframes fadeInScale {
  to {
    opacity: 1;
    transform: scale(1);
  }
}

/* Softer bounce effect */
@keyframes bounceSoft {
  0%   { transform: scale(1.03) translateY(-3px); }
  30%  { transform: scale(1.05) translateY(-5px); }
  50%  { transform: scale(1.03) translateY(-3px); }
  70%  { transform: scale(1.04) translateY(-4px); }
  100% { transform: scale(1.03) translateY(-3px); }
}

/* MODAL IMAGE: 80% of viewport for desktop/tablet */
.modal {
  display: none;
  position: fixed;
  z-index: 9999;
  left: 0;
  top: 0;
  width: 100vw;
  height: 100vh;
  overflow: auto;
  background: rgba(0,0,0,0.9);
}
.modal-content {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  max-width: 80vw;
  max-height: 80vh;
  object-fit: contain;
  background: #000;
  margin: 0;
  display: block;
  border-radius: 0;
  box-shadow: none;
}
.close {
  position: absolute;
  top: 50px;
  right: 50px;
  color: #fff;
  font-size: 40px;
  font-weight: bold;
  cursor: pointer;
}
.close:hover {color:#ccc;}

@keyframes shake {
  0%{transform: rotate(0deg);}
  25%{transform: rotate(10deg);}
  50%{transform: rotate(-10deg);}
  75%{transform: rotate(10deg);}
  100%{transform: rotate(0deg);}
}

@media (max-width: 720px) {
  .product {width: 99vw;}
  .product img {height: 180px;}
  #cart-panel {width: 95vw; left: 2vw;}
  .theme-switcher {width: 95vw; left: 2vw; transform: none;}
  .modal-content {
    max-width: 90vw;
    max-height: 65vh;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
  .close {top: 20px; right: 20px; font-size: 32px;}
}

body.dark {
  --bg: #181a20;
  --text: #f6f6f6;
  --accent: #4f8cff;
  --input-bg: #26272c;
  --cart-bg: #23252a;
  --cart-text: #f6f6f6;
}
</style>
</head>
<body>

<header>
  <img src="https://raw.githubusercontent.com/Amuya12/bannerimage/main/IMG-20250813-WA0002%5B1%5D.jpg" alt="G-Shine Hardware Banner">
  <h1>G-Shine Hardware</h1>
  <p class="tagline">Plumbing Materials • Sanitary wares • Tools — All in One Place</p>
</header>

<div class="search-container">
  <input type="text" id="search" placeholder="Search products...">
  <ul id="search-suggestions" class="search-suggestions"></ul>
</div>

<!-- CATEGORY FILTERS -->
<div class="category-filter-container">
  <button class="category-filter active" onclick="filterCategory('All')">All</button>
  <button class="category-filter" onclick="filterCategory('bathroom accessories')">bathroom accessories</button>
  <button class="category-filter" onclick="filterCategory('Taps')">Taps</button>
  <button class="category-filter" onclick="filterCategory('Locks & Hinges')">Locks & Hinges</button>
  <button class="category-filter" onclick="filterCategory('Electrical')">Electrical</button>
  <button class="category-filter" onclick="filterCategory('Tiles')">Tiles</button>
  <button class="category-filter" onclick="filterCategory('Granite & Marble')">Granite & Marble</button>
  <button class="category-filter" onclick="filterCategory('Gypsum')">Gypsum</button>
  <button class="category-filter" onclick="filterCategory('Paints')">Paints</button>
  <button class="category-filter" onclick="filterCategory('Tools')">Tools</button>
</div>

<!-- PRODUCT LIST -->
<div class="product-list-container">
  <div class="products" id="product-list">
    <div class="product" data-id="6-Hook" data-category="bathroom accessories" data-name="Hooks">
      <img src="6-Hook.jpg" alt="6-Hook" onclick="openModal(this)">
      <div>6-Hook</div>
      <div class="price">KSh 1000</div>
      <button type="button" class="cart" onclick="orderNow('6-Hook')">Add to Cart</button>
    </div>
 <div class="product" data-id="bathroom accessory" data-category="bathroom accessories" data-name="Bathroom Accessory">
      <img src="Bathroom Accessory.jpg" alt="bathroom accessory" onclick="openModal(this)">
      <div>bathroom accessory</div>
      <div class="price">KSh 2500</div>
      <button type="button" class="cart" onclick="orderNow('bathroom accessory')">Add to Cart</button>
    </div>  
 <div class="product" data-id="Bathroom accessory big black and gold" data-category="bathroom accessories" data-name="Bathroom accessory big black and gold">
      <img src="Bathroom accessory big black and gold.jpeg" alt="Bathroom accessory big black and gold" onclick="openModal(this)">
      <div>Bathroom accessory big black and gold</div>
      <div class="price">KSh 4800</div>
      <button type="button" class="cart" onclick="orderNow('bathroom accessory')">Add to Cart</button>
    </div>
 <div class="product" data-id="Bathroom accessory big maat black" data-category="bathroom accessories" data-name="Bathroom accessory big maat black">
      <img src="Bathroom accessory big maat black.jpeg" alt="Bathroom accessory big maat black" onclick="openModal(this)">
      <div>Bathroom accessory big maat black</div>
      <div class="price">KSh 4800</div>
      <button type="button" class="cart" onclick="orderNow('Bathroom accessory big maat black')">Add to Cart</button>
    </div>
  <div class="product" data-id="Bathroom Accessory Black" data-category="bathroom accessories" data-name="Bathroom Accessory Black">
      <img src="Bathroom Accessory Black.jpg" alt="Bathroom Accessory Black" onclick="openModal(this)">
      <div>Bathroom Accessory Black</div>
      <div class="price">KSh 4200</div>
      <button type="button" class="cart" onclick="orderNow('Bathroom Accessory Black')">Add to Cart</button>
    </div>
 <div class="product" data-id="Bathroom accessory chrome" data-category="bathroom accessories" data-name="Bathroom accessory chrome">
      <img src="Bathroom accessory chrome.jpeg" alt="Bathroom accessory chrome" onclick="openModal(this)">
      <div>Bathroom accessory chrome</div>
      <div class="price">KSh 4300</div>
      <button type="button" class="cart" onclick="orderNow('Bathroom accessory chrome')">Add to Cart</button>
    </div>
 <div class="product" data-id="Bathroom Accessory Executive" data-category="bathroom accessories" data-name="Bathroom Accessory Executive">
      <img src="Bathroom Accessory Executive.jpg" alt="Bathroom Accessory Executive" onclick="openModal(this)">
      <div>Bathroom Accessory Executive</div>
      <div class="price">KSh 5800</div>
      <button type="button" class="cart" onclick="orderNow('Bathroom Accessory Executive')">Add to Cart</button>
    </div>
 <div class="product" data-id="Bathroom Accessory Small" data-category="bathroom accessories" data-name="Bathroom Accessory Small">
      <img src="Bathroom Accessory Small.jpg" alt="Bathroom Accessory Small" onclick="openModal(this)">
      <div>Bathroom Accessory Small</div>
      <div class="price">KSh 2200</div>
      <button type="button" class="cart" onclick="orderNow('Bathroom Accessory Small')">Add to Cart</button>
    </div>  
<div class="product" data-id="brasstap" data-category="Plumbing" data-name="Brass Tap">
      <img src="Lincy-brass-lock-900-300x300.jpg" alt="Brass Tap" onclick="openModal(this)">
      <div>Brass Tap</div>
      <div class="price">KSh 500</div>
      <button type="button" class="cart" onclick="orderNow('brasstap')">Add to Cart</button>
    </div>
    <div class="product" data-id="mixertap" data-category="Taps" data-name="Mixer Tap">
      <img src="https://i.imgur.com/zZ7GvKX.jpeg" alt="Mixer Tap" onclick="openModal(this)">
      <div>Mixer Tap</div>
      <div class="price">KSh 1500</div>
      <button type="button" class="cart" onclick="orderNow('mixertap')">Add to Cart</button>
    </div>
    <div class="product" data-id="sinktap" data-category="Taps" data-name="Sink Tap">
      <img src="sink.jpg" alt="Sink Tap" onclick="openModal(this)">
      <div>Sink Tap</div>
      <div class="price">KSh 800</div>
      <button type="button" class="cart" onclick="orderNow('sinktap')">Add to Cart</button>
    </div>
    <div class="product" data-id="padlock" data-category="Locks & Hinges" data-name="Padlock">
      <img src="https://i.imgur.com/TK1Bfjq.jpeg" alt="Padlock" onclick="openModal(this)">
      <div>Padlock</div>
      <div class="price">KSh 600</div>
      <button type="button" class="cart" onclick="orderNow('padlock')">Add to Cart</button>
    </div>
    <div class="product" data-id="doorhinges" data-category="Locks & Hinges" data-name="Door Hinges">
      <img src="https://i.imgur.com/UG2RL6Q.jpeg" alt="Door Hinges" onclick="openModal(this)">
      <div>Door Hinges</div>
      <div class="price">KSh 400</div>
      <button type="button" class="cart" onclick="orderNow('doorhinges')">Add to Cart</button>
    </div>
    <div class="product" data-id="ledbulb" data-category="Electrical" data-name="LED Bulb">
      <img src="https://i.imgur.com/FZNRjnp.jpeg" alt="LED Bulb" onclick="openModal(this)">
      <div>LED Bulb</div>
      <div class="price">KSh 250</div>
      <button type="button" class="cart" onclick="orderNow('ledbulb')">Add to Cart</button>
    </div>
    <div class="product" data-id="extensioncable" data-category="Electrical" data-name="Extension Cable">
      <img src="https://i.imgur.com/E2S5ch6.jpeg" alt="Extension Cable" onclick="openModal(this)">
      <div>Extension Cable</div>
      <div class="price">KSh 1200</div>
      <button type="button" class="cart" onclick="orderNow('extensioncable')">Add to Cart</button>
    </div>
    <div class="product" data-id="floortile" data-category="Tiles" data-name="Floor Tile">
      <img src="https://i.imgur.com/6rIYm9U.jpeg" alt="Floor Tile" onclick="openModal(this)">
      <div>Floor Tile</div>
      <div class="price">KSh 950</div>
      <button type="button" class="cart" onclick="orderNow('floortile')">Add to Cart</button>
    </div>
    <div class="product" data-id="walltile" data-category="Tiles" data-name="Wall Tile">
      <img src="https://i.imgur.com/mvS7f4Q.jpeg" alt="Wall Tile" onclick="openModal(this)">
      <div>Wall Tile</div>
      <div class="price">KSh 700</div>
      <button type="button" class="cart" onclick="orderNow('walltile')">Add to Cart</button>
    </div>
    <div class="product" data-id="graniteslab" data-category="Granite & Marble" data-name="Granite Slab">
      <img src="https://i.imgur.com/tXpmRcd.jpeg" alt="Granite Slab" onclick="openModal(this)">
      <div>Granite Slab</div>
      <div class="price">KSh 5500</div>
      <button type="button" class="cart" onclick="orderNow('graniteslab')">Add to Cart</button>
    </div>
    <div class="product" data-id="marbleslab" data-category="Granite & Marble" data-name="Marble Slab">
      <img src="https://i.imgur.com/GF6k64n.jpeg" alt="Marble Slab" onclick="openModal(this)">
      <div>Marble Slab</div>
      <div class="price">KSh 6000</div>
      <button type="button" class="cart" onclick="orderNow('marbleslab')">Add to Cart</button>
    </div>
    <div class="product" data-id="gypsumboard" data-category="Gypsum" data-name="Gypsum Board">
      <img src="https://i.imgur.com/gJSpZ0r.jpeg" alt="Gypsum Board" onclick="openModal(this)">
      <div>Gypsum Board</div>
      <div class="price">KSh 1500</div>
      <button type="button" class="cart" onclick="orderNow('gypsumboard')">Add to Cart</button>
    </div>
    <div class="product" data-id="whitepaint20l" data-category="Paints" data-name="White Paint (20L)">
      <img src="https://i.imgur.com/3tX8USy.jpeg" alt="White Paint" onclick="openModal(this)">
      <div>White Paint (20L)</div>
      <div class="price">KSh 3500</div>
      <button type="button" class="cart" onclick="orderNow('whitepaint20l')">Add to Cart</button>
    </div>
    <div class="product" data-id="bluepaint20l" data-category="Paints" data-name="Blue Paint (20L)">
      <img src="https://i.imgur.com/RPZ14Oa.jpeg" alt="Blue Paint" onclick="openModal(this)">
      <div>Blue Paint (20L)</div>
      <div class="price">KSh 3700</div>
      <button type="button" class="cart" onclick="orderNow('bluepaint20l')">Add to Cart</button>
    </div>
    <div class="product" data-id="hammer" data-category="Tools" data-name="Hammer">
      <img src="https://i.imgur.com/pCkqHGY.jpeg" alt="Hammer" onclick="openModal(this)">
      <div>Hammer</div>
      <div class="price">KSh 450</div>
      <button type="button" class="cart" onclick="orderNow('hammer')">Add to Cart</button>
    </div>
    <div class="product" data-id="screwdriverset" data-category="Tools" data-name="Screwdriver Set">
      <img src="https://i.imgur.com/R4wbpKN.jpeg" alt="Screwdriver Set" onclick="openModal(this)">
      <div>Screwdriver Set</div>
      <div class="price">KSh 900</div>
      <button type="button" class="cart" onclick="orderNow('screwdriverset')">Add to Cart</button>
    </div>
  </div>
  <!-- Pager Controls -->
  <div id="pager-controls" style="text-align:center; margin:2em 0 1em 0; display:none;">
    <button id="prevBtn" style="padding:0.4em 1em; margin-right:10px; border-radius:8px; border:1px solid #ccc;">Previous</button>
    <span id="pager-status" style="font-weight:bold;"></span>
    <button id="nextBtn" style="padding:0.4em 1em; margin-left:10px; border-radius:8px; border:1px solid #ccc;">Next</button>
  </div>
</div>

<!-- Product Image Modal -->
<div id="imgModal" class="modal">
  <span class="close" id="closeModalBtn">&times;</span>
  <img class="modal-content" id="modalImg">
</div>

<!-- Floating WhatsApp Button -->
<a id="whatsapp-float" href="https://wa.me/254111256585?text=Hello%20G-Shine%20Hardware!" target="_blank">
  <img src="https://upload.wikimedia.org/wikipedia/commons/6/6b/WhatsApp.svg" alt="WhatsApp" style="width:30px;height:30px;">
</a>

<!-- Floating Cart Icon -->
<div id="floating-cart" onclick="toggleCart()">
  🛒 <span id="cart-count">0</span>
</div>
<!-- Cart Panel (only ONE!) -->
<div id="cart-panel">
  <h4>Your Cart (Quote)</h4>
  <ul id="cart-items"></ul>
  <p><strong>Total:</strong> <span id="cart-total">KSh 0</span></p>
  <button type="button" onclick="checkoutCart()">Send Quote via WhatsApp</button>
</div>

<!-- Theme Switcher -->
<div class="theme-switcher">
  <span>Theme:</span>
  <button id="theme-light" onclick="setTheme('light')">Light</button>
  <button id="theme-dark" onclick="setTheme('dark')">Dark</button>
</div>

<script>
// Theme Switcher
function setTheme(theme) {
  if (theme === 'dark') {
    document.body.classList.add('dark');
    document.getElementById('theme-dark').classList.add('active');
    document.getElementById('theme-light').classList.remove('active');
    localStorage.setItem('theme', 'dark');
  } else {
    document.body.classList.remove('dark');
    document.getElementById('theme-light').classList.add('active');
    document.getElementById('theme-dark').classList.remove('active');
    localStorage.setItem('theme', 'light');
  }
}
if(localStorage.getItem('theme')==='dark'){setTheme('dark');}else{setTheme('light');}

// CATEGORY FILTER
function filterCategory(cat) {
  document.querySelectorAll('.category-filter').forEach(btn => {
    btn.classList.toggle('active', btn.textContent === cat);
  });
  // show first page after category change
  showProductsPage(1);
}

// Sticky search suggestions logic
const products = Array.from(document.querySelectorAll('.product')).map(prod => ({
  id: prod.getAttribute('data-id'),
  name: prod.getAttribute('data-name'),
  img: prod.querySelector('img').src,
  price: prod.querySelector('.price').textContent.trim(),
  category: prod.getAttribute('data-category')
}));

const searchInput = document.getElementById('search');
const suggestionsEl = document.getElementById('search-suggestions');

searchInput.addEventListener('input', function() {
  const query = this.value.trim().toLowerCase();
  if (query) {
    const matches = products.filter(p => p.name.toLowerCase().includes(query));
    if (matches.length > 0) {
      suggestionsEl.innerHTML = matches.map(p =>
        `<li onclick="selectSuggestion('${p.id}')">
          <img src="${p.img}" style="width:22px;height:22px;vertical-align:middle;border-radius:4px;margin-right:6px;">
          <span>${highlightMatch(p.name, query)}</span>
          <span style="float:right;color:#2196f3;font-weight:bold;">${p.price}</span>
          <span style="float:right; margin-right:12px; color:#555; font-size:0.9em;">${p.category}</span>
        </li>`
      ).join('');
      suggestionsEl.style.display = 'block';
    } else {
      suggestionsEl.innerHTML = `<li style="color:#999;">No matches found</li>`;
      suggestionsEl.style.display = 'block';
    }
  } else {
    suggestionsEl.style.display = 'none';
  }

  document.querySelectorAll('.product').forEach(prod => {
    const name = prod.getAttribute('data-name').toLowerCase();
    prod.style.display = (!query || name.includes(query)) ? "inline-block" : "none";
    prod.querySelectorAll('div').forEach(el => {
      el.innerHTML = el.textContent.replace(new RegExp(query, "gi"), match => `<span class="highlight">${match}</span>`);
    });
  });
});
searchInput.addEventListener('blur', function() {
  setTimeout(() => { suggestionsEl.style.display = 'none'; }, 200);
});
function highlightMatch(text, query) {
  return text.replace(new RegExp(query, "gi"), match => `<span class="highlight">${match}</span>`);
}
function selectSuggestion(id) {
  searchInput.value = products.find(p => p.id === id).name;
  suggestionsEl.style.display = 'none';
  document.querySelectorAll('.product').forEach(prod => {
    prod.style.display = (prod.getAttribute('data-id') === id) ? "inline-block" : "none";
  });
}
setInterval(() => {
  const btn = document.getElementById('whatsapp-float');
  btn.style.animation = "shake 0.4s";
  setTimeout(() => { btn.style.animation = ""; }, 400);
}, 4000);

// --- MODAL LOGIC ---
function openModal(img) {
  var modal = document.getElementById('imgModal');
  var modalImg = document.getElementById('modalImg');
  modalImg.src = img.src;
  modalImg.alt = img.alt;
  modal.style.display = "block";
}
document.getElementById('closeModalBtn').onclick = function() {
  document.getElementById('imgModal').style.display = "none";
  document.getElementById('modalImg').src = "";
};
document.getElementById('imgModal').onclick = function(e) {
  if (e.target === this) {
    this.style.display = "none";
    document.getElementById('modalImg').src = "";
  }
};

// --- CART FUNCTIONALITY WITH STABLE PRODUCT IDs ---
let cart = [];

function orderNow(productId) {
  let productEl = document.querySelector(`.product[data-id="${productId}"]`);
  if (!productEl) return;
  const name = productEl.getAttribute('data-name');
  const priceText = productEl.querySelector('.price').textContent.replace(/[^\d]/g, '');
  const price = parseInt(priceText, 10);

  const existing = cart.find(item => item.id === productId);
  if (existing) {
    existing.quantity += 1;
    existing.name = name; // update to latest name, always
  } else {
    cart.push({
      id: productId,
      name: name,
      quantity: 1,
      price: price
    });
  }
  updateCartUI();
  document.getElementById('cart-panel').style.display = 'block';
}

function updateCartUI() {
  const cartCount = cart.reduce((sum, item) => sum + item.quantity, 0);
  document.getElementById('cart-count').textContent = cartCount;

  const cartList = document.getElementById('cart-items');
  cartList.innerHTML = '';
  let total = 0;
  cart.forEach((item, index) => {
    // Display latest name from DOM, so you can freely change product names
    const productEl = document.querySelector(`.product[data-id="${item.id}"]`);
    if(productEl) item.name = productEl.getAttribute('data-name');
    const lineTotal = item.quantity * item.price;
    total += lineTotal;
    const li = document.createElement('li');
    li.innerHTML = `
      <div style="flex: 1 1 100%;">${index + 1}. ${item.name}<br>
      Qty: ${item.quantity} × KSh ${item.price} = <strong>KSh ${lineTotal}</strong></div>
      <div class="cart-controls">
        <button onclick="changeQty('${item.id}', 1)">＋</button>
        <button onclick="changeQty('${item.id}', -1)">－</button>
        <button onclick="removeItem('${item.id}')">🗑</button>
      </div>
    `;
    cartList.appendChild(li);
  });
  document.getElementById('cart-total').textContent = `KSh ${total}`;
}

function changeQty(id, delta) {
  const item = cart.find(i => i.id === id);
  if (!item) return;
  item.quantity += delta;
  if (item.quantity <= 0) {
    cart = cart.filter(i => i.id !== id);
  }
  updateCartUI();
}

function removeItem(id) {
  cart = cart.filter(i => i.id !== id);
  updateCartUI();
}

function toggleCart() {
  const panel = document.getElementById('cart-panel');
  panel.style.display = panel.style.display === 'block' ? 'none' : 'block';
}

function checkoutCart() {
  if (cart.length === 0) {
    alert("Your cart is empty.");
    return;
  }
  let message = "";
  let total = 0;
  if (cart.length === 1) {
    const item = cart[0];
    total = item.price * item.quantity;
    message = `Hello G-Shine Hardware! I would like to have this item:\n${item.name} — Qty: ${item.quantity} x KSh ${item.price} = KSh ${total}`;
  } else {
    message = `Hello G-Shine Hardware! I would like a quotation for:\n`;
    cart.forEach((item, i) => {
      const lineTotal = item.quantity * item.price;
      total += lineTotal;
      message += `${i + 1}. ${item.name} — Qty: ${item.quantity} x KSh ${item.price} = KSh ${lineTotal}\n`;
    });
    message += `\nTotal: KSh ${total}`;
  }
  const phone = "254111256585";
  const url = `https://wa.me/${phone}?text=${encodeURIComponent(message)}`;
  window.open(url, '_blank');
}

// --- PAGINATION LOGIC ---
const MAX_ITEMS_PER_PAGE = 20;
let currentPage = 1;

function getActiveCategory() {
  let activeCatBtn = document.querySelector('.category-filter.active');
  return activeCatBtn ? activeCatBtn.textContent : 'All';
}

function getProductsInCategory(category) {
  return Array.from(document.querySelectorAll('.product'))
    .filter(prod => category === 'All' || prod.getAttribute('data-category') === category);
}

function showProductsPage(page = 1) {
  const category = getActiveCategory();
  const productsInCat = getProductsInCategory(category);
  const totalItems = productsInCat.length;
  const totalPages = Math.ceil(totalItems / MAX_ITEMS_PER_PAGE) || 1;

  // Hide all products
  document.querySelectorAll('.product').forEach(prod => prod.style.display = 'none');

  // Show current page's products
  const start = (page - 1) * MAX_ITEMS_PER_PAGE;
  const end = start + MAX_ITEMS_PER_PAGE;
  productsInCat.slice(start, end).forEach(prod => prod.style.display = "inline-block");

  // Pager controls
  const pagerControls = document.getElementById('pager-controls');
  const pagerStatus = document.getElementById('pager-status');
  pagerControls.style.display = (totalItems > MAX_ITEMS_PER_PAGE) ? 'block' : 'none';
  pagerStatus.textContent = `Page ${page} of ${totalPages}`;

  // Enable/disable buttons
  document.getElementById('prevBtn').disabled = (page === 1);
  document.getElementById('nextBtn').disabled = (page === totalPages);

  currentPage = page;
}

// Pager button listeners
document.getElementById('prevBtn').onclick = function() {
  if (currentPage > 1) showProductsPage(currentPage - 1);
};
document.getElementById('nextBtn').onclick = function() {
  const category = getActiveCategory();
  const productsInCat = getProductsInCategory(category);
  const totalPages = Math.ceil(productsInCat.length / MAX_ITEMS_PER_PAGE) || 1;
  if (currentPage < totalPages) showProductsPage(currentPage + 1);
};

// Update page on category change (already handled in filterCategory)
document.querySelectorAll('.category-filter').forEach(btn => {
  btn.addEventListener('click', () => {
    setTimeout(() => showProductsPage(1), 10);
  });
});

// Show first page on load
showProductsPage(1);
<script>
document.querySelectorAll('.product img').forEach((img, index) => {
  img.style.animationDelay = `${index * 0.1}s`;
});
</script>
</body>
</html>
