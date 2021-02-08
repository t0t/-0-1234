<script>
  import P5 from 'p5-svelte'
  let width = 0
  let height = 0

  const sketch = (p5) => {
    p5.setup = () => {
      p5.createCanvas(width, height)
    }

    p5.draw = () => {
      p5.ellipse(p5.width, p5.height, width, height)
      p5.line(0, 0, 400, 400)
      p5.line(0, 400, 400, 0)
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


<div class="canvas" bind:clientWidth={width} bind:clientHeight={height}>
  <div class="over">
    <h1>Diseño generativo</h1>

      <input type="range" bind:value={width} min="100" max="1000" step="0.01" />
      {width}

      <input
        type="range"
        bind:value={height}
        min="100"
        max="1000"
        step="0.01" />
      {height}

	  
  </div>

  <P5 {sketch} />
</div>
