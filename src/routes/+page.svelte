<script lang="ts">
	import logo from '$lib/images/logo.png';
	import { fade, fly } from 'svelte/transition';
	import { onMount } from 'svelte';
	import Link from '../shared/Link.svelte';
	import ConferenceThemes from '../section/ConferenceThemes.svelte';
	import Hero from '../section/Hero.svelte';
	import Buy from '../section/Buy.svelte';

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

<Hero />
<ConferenceThemes />
<Buy />
