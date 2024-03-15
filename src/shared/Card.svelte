<script lang="ts">
	import Youtube from './icons/Youtube.svelte';
	import Tiktok from './icons/Tiktok.svelte';
	import Instagram from './icons/Instagram.svelte';
	export let imageUrl = '';
	export let title = '';
	export let description = '';
	export let youtube = 0;
	export let tiktok = 0;
	export let instagram = 0;
	function formatSubscribers(subscribers: number): string {
		const scale =
			subscribers > 1_000_000
				? { divisor: 1_000_000, suffix: 'm' }
				: subscribers > 1_000
					? { divisor: 1_000, suffix: 'k' }
					: null;

		if (scale) {
			const formattedNumber = (subscribers / scale.divisor).toFixed(1);
			return formattedNumber.endsWith('.0')
				? `${formattedNumber.slice(0, -2)}${scale.suffix}`
				: `${formattedNumber}${scale.suffix}`;
		}

		return subscribers.toString();
	}
</script>

<div class="card card_bg">
	<div class="card__image-wrapper">
		<img src={imageUrl} alt={title} />
	</div>
	<div class="card__content">
		<h3>{title}</h3>
		<p>{description}</p>
		<div class="social">
			{#if youtube > 0}
				<div>
					<Youtube />
					<span class="subscribers">{formatSubscribers(youtube)}</span>
				</div>
			{/if}
			{#if tiktok > 0}
				<div>
					<Tiktok />
					<span class="subscribers">{formatSubscribers(tiktok)}</span>
				</div>
			{/if}
			{#if instagram > 0}
				<div>
					<Instagram />
					<span class="subscribers"> {formatSubscribers(instagram)}</span>
				</div>
			{/if}
		</div>
	</div>
</div>

<style>
	.card {
		border-radius: 4px;
		overflow: hidden;
		width: 400px;
		height: auto;
		border-radius: 30px;
		text-align: center;
	}

	@media (max-width: 768px) {
		.card {
			width: 100%;
		}
	}

	.card_bg {
		background-color: hsla(0, 0%, 100%, 0.05);
		transition-property:
			background-color,
			backdrop-filter transform;
		transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
		transition-duration: 0.15s;
		backdrop-filter: blur(8px);
	}
	.card_bg:hover {
		background-color: hsla(0, 0%, 100%, 0.1); /* More opaque on hover */
		transform: scale(1.02); /* Scale the element up on hover */
		transition-duration: 0.2s;
	}

	h3 {
		font-size: 26px;
		line-height: 1.3;
	}

	p {
		font-size: 22px;
		line-height: 1.5;
	}

	.card__image-wrapper {
		width: 100%;
		height: 500px;
		overflow: hidden;
		position: relative;
	}

	img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
		object-fit: cover;
	}

	.card__content {
		padding: 25px 15px;
	}

	.social {
		display: flex;
		justify-content: start;
		padding: 0 20px;
		align-items: center;
		gap: 20px;
		width: 100%;
		height: 75px;
	}
	.social div {
		display: flex;
		align-items: center;
		gap: 10px;
	}

	.social :global(svg) {
		width: 55px;
		height: 55px;
	}
	.subscribers {
		font-size: 24px;
		font-weight: 700;
	}
</style>
