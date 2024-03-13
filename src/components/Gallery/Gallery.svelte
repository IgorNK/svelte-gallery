<script lang="ts">
  import GalleryCard from '../Gallery-card/Gallery-card.svelte';
  export let images: Array<{
    image: string,
    title: string,
    info: string
  }>;
</script>

<div class="Gallery">
  {#each images as card, i (i)}
    <GalleryCard {...card} />
  {/each}
</div>

<style>
  .Gallery {
    margin: 0;
    padding: 0;
    width: 100vw;
    max-width: 100%;
    height: 100%;
    display: grid;
    grid-template-columns: 1fr 1fr;
  }
</style>