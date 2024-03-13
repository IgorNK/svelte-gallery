<script lang="ts">
  export let image: string;
  let numSegments: Number = 8;
  let hovered: Array<Number> = [];
  import "../../routes/index.css";
</script>

<div class="Splash" style="background-image: url({image})">
  {#each Array(numSegments) as _s, i (i)}
    <div 
      role="img" 
      on:mouseenter={() => {
        hovered = [...hovered, i]
      }} 
      class={
        hovered.includes(i) ? "Splash-segment-hovered"
        : "Splash-segment"
      } 
    />
  {/each}
  <h1 class="Splash-header">The photography of Xeniya Kolosova</h1>
  <h2 class="Splash-subheader">What I do with squirrels is my own business</h2>
</div>

<style>
  .Splash {
    width: 100vw;
    max-width: 100%;
    height: 100vh;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(0px, 1fr));
    margin: 0;
    padding: 0;
    background-size: auto 100vh;
  }

  .Splash-header {
    position: absolute;
    padding-left: 10%;
    padding-top: 20%;
    font-family: 'PlayfairDisplay', Arial, Helvetica, sans-serif;
    font-size: 48px;
  }

  .Splash-subheader {
    position: absolute;
    padding-left: 10%;
    padding-bottom: 20%;
    bottom: 0;
    font-family: 'Alegreya', Arial, Helvetica, sans-serif;
    font-size: 28px;
    text-shadow: 6px 6px 20px #fff,
    -4px 2px 30px #fff;
  }

  .Splash-segment {
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    transition: 0.2s ease-in-out;
    margin: 0;
    padding: 0;
    z-index: 9;
  }

  .Splash-segment-hovered {
    background-color: rgba(0, 0, 0, 0);
    transition: 0.2s ease-in-out;
  }
</style>