<script>
  import './index.css';
</script>

<div class="app">
	<main>
		<slot />
	</main>
</div>

<style>  
  .app {
    margin: 0;
    padding: 0;
		min-height: 100vh;
	}

	main {
		display: flex;
		flex-direction: column;
		width: 100%;
		max-width: 100%;
    margin: 0;
    padding: 0;
		box-sizing: border-box;
	}

	@media (min-width: 480px) {

	}
</style>
