<script>
	let selectedColor = "#ffffff";
  
	// @ts-ignore
	function updateColor(event) {
	  selectedColor = event.target.value;
	}
  
	$: rgbValue = getRGB(selectedColor);
	$: hexValue = selectedColor;
  
	// @ts-ignore
	function getRGB(hexColor) {
	  // Convert HEX to RGB
	  const hex = hexColor.replace(/^#/, '');
	  const bigint = parseInt(hex, 16);
	  const r = (bigint >> 16) & 255;
	  const g = (bigint >> 8) & 255;
	  const b = bigint & 255;
	  return `${r}, ${g}, ${b}`;
	}
  </script>
  
  
  <style>
	* {
	  margin: 0;
	  padding: 0;
	  box-sizing: border-box;
	}
  
	/* Basic styling */
	.html {
	  font-family: Arial, sans-serif;
	  background-image: linear-gradient(rgba(18, 41, 125, 1), rgba(18, 41, 125, 0));
	}
  
	img {
	  width: 300px;
	}
  
	header {
	  /* background-color: #0D1D59; */
	  color: #fff;
	  padding: 30px 0;
	  display: flex;
	  justify-content: space-between;
	  align-items: center;
	  box-shadow: 0 0 5px rgba(0, 0, 0, 0.5);
	}
  
	.logo h1 {
	  font-size: 2rem;
	  margin-left: 20px;
	}
  
	nav ul {
	  list-style: none;
	  display: flex;
	  margin-right: 20px;
	}
  
	nav ul li {
	  margin: 0 10px;
	}
  
	nav ul li a {
	  text-decoration: none;
	  color: #fff;
	  font-weight: bold;
	}
  
	main {
	  max-width: 1200px;
	  margin: 0 auto;
	  padding: 20px;
	}
  
	.hero {
	  background-color: transparent;
	  color: #fff;
	  font-size: 1.5rem;
	  padding: 20px;
	  border-radius: 5px;
	  text-align: center;
	}
  
	.hero h2 {
	  font-size: 5rem;
	  padding-bottom: 10px;
	}
  
	.cta-button {
	  display: inline-block;
	  background-color: transparent;
	  color: #151515;
	  padding: 10px 20px;
	  margin-top: 20px;
	  border-color: #151515;
	  border-style: solid;
	  border-radius: 8px;
	  text-decoration: none;
	  font-weight: bold;
	}
  
	.hero .cta-button {
	  background-color: transparent;
	  color: #ffffff;
	  border-color: #ffffff;
	}
  
	.features {
	  display: block;
	  justify-content: space-between;
	  margin: 20px;
	}
  
	.feature {
	  flex: 1;
	  background-color: #e1eff8;
	  padding: 50px;
	  border-radius: 5px;
	  text-align: center;
	  margin: 50px;
	  box-shadow: 0 0 5px rgba(0, 0, 0, 0.2);
	}
  
	.feature img {
	  float: left;
	  margin-top: 10px;
	}
  
	.feature i {
	  font-size: 2rem;
	  margin-bottom: 10px;
	}
  
	.feature h3 {
	  font-size: 2.5rem;
	}
  
	.feature p {
	  font-size: 1.5rem;
	}
  
	.footer {
	  text-align: center;
	  background-color: #333;
	  color: #fff;
	  padding: 10px 0;
	}
  
	#color-picker-input {
	  margin-left: 150px;
	  margin-top: 15px;
	  text-align: center;
	  width: 50px;
	  height: 30px;
	  border-radius: 5px;
	}
  
	#color-preview {
	  width: 200px;
	  height: 150px;
	  float: left;
	  margin-top: -150px;
	  margin-left: 230px;
	  margin-right: 20px;
	  border-radius: 10px;
	  border: 1px solid #ccc;
	  box-shadow: 0 0 5px rgba(0, 0, 0, 0.2);
	}
  
	#color-values {
	  font-size: 1.2rem;
	  margin-top: 20px;
	  margin-left: 20px;
	  display: block;
	  margin-left: 150px;
	}
  
	#rgb-value,
	#hex-value {
	  font-weight: bold;
	}
  
	.abc p {
	  padding: 10px;
	  text-align: center;
	}
  </style>
  
  <section class="html"> 
	<header>
		<div class="logo">
		<h1>Color Tools</h1>
		</div>
		<nav>
		<ul>
			<li><a href="#">Home</a></li>
			<li><a href="#">Palette</a></li>
			<li><a href="#">About</a></li>
		</ul>
		</nav>
	</header>
	<main>
		<section class="hero">
		<h2>Color Details</h2>
		<p>Make the most out of your favorite colors. Explore now!</p>
		</section>
		<section class="features">
		<div class="feature abc">
			<i class="Color_Details"></i>
			<h3>Color Palette</h3>
			<p class="pick">Pick A color!</p>
			<input type="color" bind:value={selectedColor} on:input={updateColor} id="color-picker-input">
			<div id="color-values">
			<p>RGB: <span id="rgb-value">{rgbValue}</span></p>
			<p>HEX: <span id="hex-value">{hexValue}</span></p>
			</div>
			<div id="color-preview" style="background-color: {selectedColor}"></div>
		</div>
		</section>
	</main>
	<footer>
		<p>&copy; 2023 Color Tools</p>
	</footer>
  </section>


  
  
  