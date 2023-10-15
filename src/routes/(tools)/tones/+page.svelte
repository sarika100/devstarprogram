<script>
	// defining color tones
	let selectedVariations = 2;
	let colorTones = [
		{ name: 'Tone 1', hex: '#1881eb' },
		{ name: 'Tone 2', hex: '#2b7fd3' },
		{ name: 'Tone 3', hex: '#3e7dbc' },
		{ name: 'Tone 4', hex: '#517ba5' },
		{ name: 'Tone 5', hex: '#3e7dbc' },
		{ name: 'Tone 6', hex: '#3e7dbc' },
		{ name: 'Tone 7', hex: '#3e7dbc' },
		{ name: 'Tone 8', hex: '#3e7dbc' },
		{ name: 'Tone 9', hex: '#3e7dbc' },
		{ name: 'Tone 10', hex: '#3e7dbc' }
	];
	function handleVariationsClick(variation) {
		selectedVariations = variation;
	}

	function handleClick() {
		alert('Button clicked!');
	}
	let showColorPicker = false; // Controls the visibility of the color picker

	function toggleColorPicker() {
		showColorPicker = !showColorPicker;
	}

	function handleColorPickerChange(event) {
		const selectedColor = event.target.value; // Get the selected color from the color picker
		colorTones = colorTones.map((tone) => ({
			...tone,
			hex: selectedColor
		})); // Update the colorTones array with the selected color
	}
</script>

<h1>Tones</h1>
<p>Add a neutral gray to your colours.</p>

<div class="container">
	<div class="colour-input">
		<h3>Colour</h3>
		<label for="color">Hex Colour:</label>
		<input
			id="color"
			placeholder="#00ff00"
			autocapitalize="off"
			autocomplete="off"
			spellcheck="off"
			width="5px"
			height="6px"
			type="text"
		/>
		<button class="color-picker-container" on:click={toggleColorPicker}>CP</button>
		<div class="color-picker-container">
			{#if showColorPicker}
				<input type="color" on:change={handleColorPickerChange} />
			{/if}
		</div>
	</div>

	<div class="color-tones">
		{#each colorTones.slice(0, selectedVariations) as tone}
			<div class="color-tone" style="background-color: {tone.hex}">
				{tone.name}
			</div>
		{/each}
	</div>
</div>

<div class="variations-export-container">
	<div class="variations">
		<h3>Variations</h3>
		{#each [2, 4, 5, 8, 10] as variation}
			<button
				class="variation-button"
				on:click={() => handleVariationsClick(variation)}
				title="{variation} variations">{variation}</button
			>
		{/each}
	</div>

	<div class="export-selections">
		<h3>Export Selections</h3>
		<button on:click={handleClick} title="Export as CSS">CSS</button>
		<button on:click={handleClick} title="Export as SCSS">SCSS</button>
		<button on:click={handleClick} title="Export as JS">JS</button>
		<button on:click={handleClick} title="Export as SVG">SVG</button>
		<button on:click={handleClick} title="Export as PNG">PNG</button>
	</div>
</div>

<style>
	@import './stylesheet.css';

	@import url('https://fonts.googleapis.com/css2?family=Josefin+Sans&family=Libre+Baskerville:ital,wght@0,400;0,700;1,400&family=Poppins&display=swap');
</style>
