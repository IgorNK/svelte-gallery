<script lang="ts">
  import GalleryImage from "../Gallery-image/Gallery-image.svelte";
  import type { Image } from '../../types/image.type';
  export let pair: Array<Image | null>;
  enum Side {
    Left,
    Right
  };
  let selected: number = -1;
  let getSide: (slected: Side | null) => string = (selected: Side | null) => {
    let style: string;
    switch (selected) {
      case 0: {
        style = "CardInfo-left";
        break;
      }
      case 1: {
        style = "CardInfo-right";
        break;
      }
      default: {
        style = "CardInfo-hidden";
        break;
      }
    }
    return style;
  }
  
</script>

<div 
  role="img" 
  class="GalleryCard"
  on:mouseleave={() => {
    selected = -1;
    console.log(selected);
  }}  
>  
  {#each pair as image, i (i)}    
    {#if image !== null}
      <GalleryImage 
        {...image} 
        on:mouseenter={() => {
          selected = i;
          console.log(selected);
        }} 
      />
    {/if}      
  {/each} 
  <div class={getSide(selected)}>
    <h3 class="CardInfo-title">
      {selected !== -1 ? pair[selected].title : ""}
    </h3>
  </div>
</div> 

<style>
  .GalleryCard {
    width: 100%;
    height: 100%;
    position: relative;
    display: flex;
    flex-direction: row;
    align-items: center;
    overflow: hidden;
  }

  .CardInfo-hidden {
    width: 100%;
    height: 100%;
    position: absolute;
    transform: translate(0, 0);
    background-color: rgba(0, 0, 0, 0.3);
    transition: 1s ease-in-out;
    pointer-events: none;
  }

  .CardInfo-left {
    width: 50%;
    height: 100%;
    transform: translate(100%, 0);
    position: absolute;
    background-color: rgba(0, 0, 0, 1);
    transition: 1s ease-in-out;
    pointer-events: none;
  }

  .CardInfo-right {
    width: 50%;
    height: 100%;
    transform: translate(0, 0);
    position: absolute;
    background-color: rgba(0, 0, 0, 1);
    transition: 1s ease-in-out;
    pointer-events: none;
  }

  .CardInfo-title {
    font-family: 'Alegreya', Arial, Helvetica, sans-serif;
    color: #fff;
    font-weight: 700;
    text-shadow: 6px 6px 20px #fff,
    -4px 2px 30px #fff;
    font-size: 24px;
    width: 100%;
    text-align: end;
  }
</style>