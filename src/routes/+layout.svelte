<script>
	import InterTightRegular from '$lib/font/InterTight-Regular.woff2';
	import InterTightSemiBold from '$lib/font/InterTight-SemiBold.woff2';
	import './styles.css';
</script>

<div class="app">
	<main>
		<slot />
	</main>
</div>

<style>
	.app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}
	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		gap: 55px;
		padding: 1rem;
		width: 100%;
		margin: 0 auto;
		box-sizing: border-box;
	}
</style>
