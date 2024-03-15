<script>
	export let sticky = false;
</script>

<h3 class="title" class:sticky>
	<slot />
</h3>

<style>
	.title {
		text-align: start;
		font-size: 65px;
		line-height: 1;
		margin: 0 15px 0 0;
	}
	.sticky {
		position: sticky;
		top: 20px;
	}
	@media (max-width: 900px) {
		.title {
			top: 40px;
			font-size: 35px;
		}
	}
</style>
