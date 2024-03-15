<script lang="ts">
	import logo from '$lib/images/logo.png';
	import { fade, fly } from 'svelte/transition';
	import { onMount } from 'svelte';
	import Link from '../shared/Link.svelte';

	let loaded = false;
	onMount(() => (loaded = true));
	let highlight_green = true;
	let highlight_pink = false;

	function highlight(color: 'green' | 'pink') {
		highlight_green = color === 'green';
		highlight_pink = color === 'pink';
	}
</script>

<svelte:head>
	<title>Nail Moment</title>
	<link
		rel="preload"
		href="src/lib/font/InterTight-Regular.woff2"
		as="font"
		crossOrigin="anonymous"
	/>
	<link rel="preload" as="image" href={logo} />
	<meta name="description" content="Nail moment" />
</svelte:head>

<section>
	<h1>
		<span class="logo">
			{#if loaded}
				<img
					src={logo}
					transition:fly={{ duration: 1200, delay: 1000, y: -2000 }}
					alt="hello"
				/>
			{/if}
		</span>
	</h1>
	<div class="highlight_bg" />
	<h2>
		{#if loaded}
			<span in:fade={{ duration: 1500, delay: 50 }} class="description__block">
				Конференція для майстрів манікюру та педикюру!
			</span>
		{/if}
	</h2>
	<div class="description__wrapper">
		{#if loaded}
			<div
				class="description"
				in:fade={{ duration: 300, delay: 2000 }}
				class:highlight_green
				class:highlight_pink
			>
				<span
					class="description__background"
					class:highlight_green
					class:highlight_pink
				/>
				<p class="description__paragraph">
					<span>
						<span class="description__block">
							<span class="highlight">Конференція</span>, на якій ти дізнаєшся
							останні трендові новини нігтьового світу, отримаєш
							<span class="highlight">натхнення</span> та піднімеш свої знання на
							новий рівень.
						</span>
						<span class="description__block">
							Ми об'єднали <span class="highlight"> найактуальніші теми </span>,
							які жоден майстер nail сервісу не може пропустити
						</span><span class="highlight">Варшава 2024</span>
					</span>
				</p>
				<div class="actions" in:fade={{ duration: 300, delay: 50 }}>
					<Link href="/registration" color={'green'} onHover={highlight}
						>Детальніше</Link
					>
					<Link href="/registration" color={'pink'} onHover={highlight}
						>Забронювати</Link
					>
				</div>
			</div>
		{/if}
		<div></div>
	</div>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 1;
		min-height: 100dvh;
		position: relative;
		gap: 50px;
	}
	.highlight_green {
		--highlight_color: var(--pink);
		--bg_color: rgba(16, 185, 129, 0.5);
	}
	.highlight_pink {
		--highlight_color: var(--green);
		--bg_color: rgba(255, 0, 255, 0.5);
	}

	.description {
		font-size: 24px;
		line-height: 1.5;
		text-align: center;
		width: 100%;
		height: 450px;
		margin: 0 25px;
		border-top: 1px solid var(--text-color-secondary);
		border-bottom: 1px solid var(--text-color-secondary);
		padding: 38px;
		position: relative;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.description__wrapper {
		height: 380px;
		width: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.description__paragraph {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.description__paragraph .highlight {
		color: var(--highlight_color);
	}

	.description__block {
		display: block;
		padding: 10px 0;
		white-space: pre-line;
		max-width: 724px;
	}
	.description__background {
		position: absolute;
		display: block;
		opacity: 0.2;
		top: -10%;
		left: 20%;
		right: 10%;
		bottom: 0;
		filter: blur(100px);
		transition: opacity 0.5s ease-in-out;
		animation: pulse 13s infinite;
		pointer-events: none;
		background-color: var(--bg_color);
	}

	.actions {
		display: flex;
		gap: 20px;
		height: 46px;
		width: 250px;
	}

	@keyframes pulse {
		0% {
			opacity: 0.2;
			transform: scale(1);
		}
		50% {
			opacity: 0.25;
			transform: scale(1.1);
		}
		100% {
			opacity: 0.2;
			transform: scale(1);
		}
	}

	h1 {
		width: 100%;
		display: flex;
		justify-content: center;
	}

	h2 {
		text-align: start;
		max-width: var(--container-width);
		width: 100%;
		font-size: 65px;
		height: 250px;
		line-height: 1;
		padding-left: 25px;
		margin: 0 15px 0 0;
	}

	@media (max-width: 768px) {
		.description {
			height: auto;
			padding: 38px 25px;
		}
		.description__wrapper {
			flex-direction: column;
			height: auto;
		}
		.description__paragraph {
			flex-direction: column;
			align-items: center;
		}
		.description__block {
			max-width: 100%;
		}
		.description__background {
			display: none;
		}
		.actions {
			width: 100%;
		}
		h2 {
			font-size: 40px;
			height: auto;
			text-align: center;
			padding-left: 0;
		}
	}
	.logo {
		display: block;
		position: relative;
		width: 300px;
		padding: 30% 0 0 0;
	}

	@supports (aspect-ratio: 1/1) {
		.logo {
			aspect-ratio: 2/1;
			padding: 0;
		}
	}

	.logo img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
		object-fit: contain;
	}
</style>
