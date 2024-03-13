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
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 64rem;
    margin: 0;
    padding: 0;
		box-sizing: border-box;
	}

	@media (min-width: 480px) {

	}
</style>
