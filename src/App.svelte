<script>
	//   import p5 from 'p5'
	import P5 from 'p5-svelte'
	let width = 0
	let height = 0
	let angle = 0

	const sketch = p5 => {
		// let modelo;
		// p5.preload = () => {
		// 	modelo = loadModel()
		// }
		let cam;

		p5.setup = () => {
			p5.createCanvas(width, height, p5.WEBGL)
			cam = p5.createCapture(p5.VIDEO)
		}

		p5.draw = () => {
			// p5.ellipse(400, 200, width, height)
			// p5.line(0, 0, p5.width, p5.width)
			// p5.fill(255,0,150)
			// p5.box()
			
			// p5.ambientLight(255,255,255)
			// let dx = p5.mouseX - {width}
			// let dy = p5.mousey - {width}
			// let v = p5.createVector(dx,dy,0)
			p5.directionalLight(255,255,0)
			// p5.pointLight(255,0,0,200,0,0)
			
			p5.background(255)
			// p5.rectMode(p5.CENTER)
			p5.rotateX(angle)
			p5.rotateY(angle)
			// p5.translate(0,0, p5.mouseZ)
			// p5.rotateZ(angle)
			// p5.normalMaterial()
			p5.stroke(0)
			// p5.noStroke()
			// p5.ambientMaterial(255)
			p5.ambientLight(20,20,20)
			// p5.specularMaterial(100)
			p5.torus(80,79)

			angle += 0.02
		}

	}
</script>

<style>
	.canvas {
		width: 100vw;
		height: 100vh;
	}

	body {
		overflow: hidden;
	}

	.over {
		position: fixed;
	}
</style>

<div class="canvas" bind:clientWidth="{width}" bind:clientHeight="{height}">
	<div class="over">
		<h1>Diseño generativo</h1>

		<input type="range" bind:value="{width}" min="100" max="1000" step="0.01" />
		{width}

		<input type="range" bind:value="{height}" min="100" max="1000" step="0.01" />
		{height}
	</div>

	<P5 {sketch} />
</div>