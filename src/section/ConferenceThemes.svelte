<script>
	import Speaker from '../shared/Speaker.svelte';
	import Title from '../shared/Title.svelte';
	import { conferenceSpeakers } from '$lib/data/speakers';
</script>

<section>
	<!-- <div class="speaker__bg" /> -->
	<Title>Наші Спікери</Title>
	<div class="highlight_bg1" />
	<div class="speakers">
		{#each conferenceSpeakers as speaker}
			<div class="speaker">
				<Speaker
					imageUrl={speaker.photo}
					name={speaker.name}
					topic={speaker.topic}
					description={speaker.description}
					youtube={speaker.followersYouTube}
					tiktok={speaker.followersTikTok}
					instagram={speaker.followersInstagram}
				/>
				<div class="highlight_bg2" />
			</div>
		{/each}
	</div>
</section>

<style>
	section {
		position: relative;
		width: var(--container-width);
		margin: 0 auto;
	}

	section :global(.title) {
		margin-bottom: 50px;
		text-align: right;
	}

	.speakers {
		display: grid;
		row-gap: 150px;
		grid-template-columns: repeat(2, 1fr);
		align-items: start;
		justify-content: center;
	}

	@media (max-width: 768px) {
		.speakers {
			display: flex;
			flex-direction: column;
			gap: 70px;
		}
		.speaker {
			margin: 0 !important;
		}
	}

	.speaker {
		display: flex;
		flex-direction: column;
		justify-content: stretch;
		height: 100%;
		position: relative;
	}

	.speaker:nth-child(odd) {
		margin-bottom: 500px;
		--highlight-color: var(--pink);
	}
	.speaker:nth-child(even) {
		margin-top: 500px;
		--highlight-color: var(--green);
	}
</style>
