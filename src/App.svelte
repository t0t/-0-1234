<script>
	import P5 from 'p5-svelte';
	let width = 55;
	let height = 55;
  
	const sketch = (p5) => {
	  p5.setup = () => {
		p5.createCanvas(400, 400);
	  };
  
	  p5.draw = () => {
		p5.background(220)
		p5.ellipse(p5.width / 2, p5.height / 2, width, height);
		// console.log(p5.width)
	  };
	};
  </script>
  <style>
	  canvas {
		  width: 100%;
	  }
  </style>
  <h1>Diseño generativo</h1>
  <label>
	Width
	<input type="range" bind:value={width} min="100" max="1000" step="0.01" />
	{width}
  </label>
  
  <label>
	Height
	<input type="range" bind:value={height} min="100" max="1000" step="0.01" />
	{height}
  </label>
  
  <P5 {sketch} />