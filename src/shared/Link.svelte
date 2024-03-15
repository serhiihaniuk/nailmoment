<!-- generic link component -->
<script lang="ts">
	export let href = '';
	export let color: 'pink' | 'green' = 'green';
	export let onHover: (color: 'pink' | 'green') => void = () => {};
	function mouseover() {
		onHover && onHover(color);
	}
</script>

<a
	{href}
	class="link"
	on:mouseover={mouseover}
	on:focus={mouseover}
	class:green={color === 'green'}
	class:pink={color !== 'green'}
>
	<slot />
</a>

<style>
	.green {
		color: var(--green);
		border-color: var(--green);
	}
	.pink {
		color: var(--pink);
		border-color: var(--pink);
	}
	.link {
		display: block;
		text-decoration: none;
		font-size: 20px;
		border-bottom-width: 1px;
		border-bottom-style: solid;
		padding: 10px 10px;
		height: 45px;
		transition: border-bottom-width 0.3s ease;
		font-weight: 700;
		flex: 1 1;
	}

	.link:hover {
		border-bottom-width: 3px;
	}
</style>
