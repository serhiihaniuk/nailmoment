<script>
	import Card from './Card.svelte';
	import Title from './Title.svelte';
	export let imageUrl = '';
	export let name = '';
	export let topic = '';
	export let description = '';
	export let youtube = 0;
	export let tiktok = 0;
	export let instagram = 0;
</script>

<div class="speaker">
	<Card {imageUrl} title={topic} {description} {youtube} {tiktok} {instagram} />
	<Title sticky>{name}</Title>
</div>

<style>
	.speaker {
		display: grid;
		grid-template-columns: 1fr 100px;
	}
	.speaker :global(.title) {
		writing-mode: vertical-lr;
		height: fit-content;
	}

	@media (max-width: 768px) {
		.speaker {
			grid-template-columns: 1fr 40px;
		}

		.speaker :global(.title) {
			font-size: 30px;
			line-height: 1.1;
			margin: 0;
		}
	}

	.speaker:hover :global(.title) {
		font-variation-settings: normal;
		background-image: linear-gradient(to bottom, #34d399 20%, var(--pink));
		background-clip: text;
		color: transparent;
		transition-property:
			color,
			background-color,
			border-color,
			text-decoration-color,
			fill,
			stroke,
			opacity,
			box-shadow,
			transform,
			filter,
			backdrop-filter,
			-webkit-backdrop-filter;
		transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
		transition-duration: 0.15s;
	}
	.speaker__bg {
		position: absolute;
		opacity: 0.2;
		top: 20%;
		left: 0;
		right: 0;
		bottom: 0;
		background-color: var(--green);
		filter: blur(100px);
	}
</style>
