<script>
  let numSegments = 8;
</script>

<div class="Splash">
  {#each Array(numSegments) as _s}
    <div class="Splash-segment"></div>
  {/each}
</div>

<style>
  .Splash {
    width: 100vw;
    height: 100vh;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(0px, 1fr));
    justify-items: stretch;
    align-items: stretch;
    margin: 0;
    padding: 0;
  }

  .Splash-segment {
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    transition: 0.2s ease-in-out;
    margin: 0;
    padding: 0;
  }

  .Splash-segment:hover {
    background-color: rgba(0, 0, 0, 0);
  }
</style>