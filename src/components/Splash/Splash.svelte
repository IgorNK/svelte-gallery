<script lang="ts">
  import { quintOut } from 'svelte/easing';
  import { fade } from 'svelte/transition';
  import { onMount } from 'svelte';
  export let text: string;
  export let image: string;
  let hovered: Array<Number> = [];
  import "../../routes/index.css";

  let bgVisible = false;

  function scaleBackground(node: HTMLElement, { start, end, duration }) {
    return {
      duration,
      css: (t: number) => {
        const eased = quintOut(t);
        const scale = eased * (end - start) + start;
        return `
          background-size: auto ${scale}%;
        `;
      }
    };
  };
  
  onMount(() => {
    bgVisible = true;
  });
</script>
{#if bgVisible}
<div in:fade={{ duration: 500 }} class="Splash">  
  <div in:scaleBackground={{ duration: 5000, start: 120, end: 100 }} class="Splash-image" style="background-image: url({image})" />  
  <div class="Splash-container">
    {#each text as letter, i (i)}      
      <div 
        role="img" 
        on:mouseenter={() => {
          hovered = [...hovered, i]
        }} 
        class="Splash-segment"
      >
        <div class={
            hovered.includes(i) ? "Splash-curtain-left-opened"
            : "Splash-curtain-left"
          }  />
        {letter}
        <div class={
          hovered.includes(i) ? "Splash-curtain-right-opened"
          : "Splash-curtain-right"
        }  />
      </div>
    {/each}
  </div>
  <h2 class="Splash-subheader">What I do with squirrels is my own business</h2>
</div>
{:else}
  <div class="Splash-black-frame" />
{/if}

<style>
  .Splash {
    width: 100vw;
    max-width: 100%;
    height: 100vh;
    display: flex;
    position: relative;
    margin: 0;
    padding: 0;
    transition: opacity 0.5s;
  }

  .Splash-image {
    position: absolute;
    width: 100%;
    height: 100%;
    background-position: center;
    background-size: auto 100%;
  }

  .Splash-black-frame {
    width: 100vw;
    max-width: 100%;
    height: 100vh;
    background-color: black;
    transition: opacity 0.5s;
  }
    
  .Splash-container {
    width: 100%;
    height: 100%;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(0px, 1fr));
  }

  .Splash-subheader {
    position: absolute;
    padding-left: 10%;
    padding-bottom: 20%;
    bottom: 0;
    font-family: 'Alegreya', Arial, Helvetica, sans-serif;
    color: #fff;
    font-size: 28px;
    text-shadow: 6px 6px 20px #fff,
    -4px 2px 30px #fff;
  }

  .Splash-segment {
    width: 100%;
    height: 100%;
    transition: 0.2s ease-in-out;
    position: relative;
    margin: 0;
    padding: 0;
    z-index: 9;
    font-family: 'PlayfairDisplay', Arial, Helvetica, sans-serif;
    color: #fff;
    font-size: 48px;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    border-left: 1px solid black;
    border-right: 1px solid black;
  }

  .Splash-curtain-left {
    background-color: rgba(255, 255, 255, 0.3);
    position: absolute;
    width: 50%;
    height: 100%;
    left: 0;
    margin: 0;
    padding: 0;
  }

  .Splash-curtain-right {
    background-color: rgba(255, 255, 255, 0.3);
    position: absolute;
    width: 50%;
    height: 100%;
    right: 0;
    margin: 0;
    padding: 0;
  }

  .Splash-curtain-left-opened {
    width: 0.5%;
    height: 100%;
    position: absolute;
    left: 0;
    margin: 0;
    padding: 0;
    transition: 0.6s ease-in-out;
  }

  .Splash-curtain-right-opened {
    width: 0.5%;
    height: 100%;
    position: absolute;
    right: 0;
    margin: 0;
    padding: 0;
    transition: 0.6s ease-in-out;
  }
</style>