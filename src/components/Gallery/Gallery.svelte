<script lang="ts">
  import GalleryCard from '../Gallery-card/Gallery-card.svelte';
  import type { Image } from '../../types/image.type';
  
  export let images: Array<Image>;
  let makePairs: 
    (images: Array<Image>) => Array<Array<Image | null>> = 
    (images: Array<Image>) => {
    let pairs = [];
    for (let i = 0; i < images.length / 2 + 4; i += 2) {
      let pairElement: Array<Image | null> = [];
      images[i] ? pairElement.push(images[i]) : pairElement.push(null);
      images[i+1] ? pairElement.push(images[i+1]) : pairElement.push(null);
      pairs.push(pairElement);
    }
    return pairs;
  }
  let imagePairs = makePairs(images);
  
</script>

<div class="Gallery">
  {#each imagePairs as pair, i (i)}
    <GalleryCard {pair} />      
  {/each}
</div>

<style>
  .Gallery {
    margin: 0;
    padding: 0;
    width: 100vw;
    max-width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
  }
</style>