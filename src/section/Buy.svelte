<script>
	import Title from '../shared/Title.svelte';
	import Check from '../shared/icons/Check.svelte';
</script>

<section>
	<div class="highlight_bg" />
	<Title>
		Встигни забронювати свій квиток на найбільш ТРЕНДОВУ конференцію цього року!
	</Title>
	<div class="benefits">
		<div class="content">
			<div><Check /><span>Білет Прохід на конференцію</span></div>
		</div>
		<div class="content">
			<div>
				<Check /><span
					>Крутий нетворкінг зі спікерами та учасниками конференції</span
				>
			</div>
			<div>
				<Check /><span>Подарунки від наших спонсорів на суму понад 200zł</span>
			</div>
		</div>
		<div class="content">
			<div>
				<Check /><span>Кава-брейк і нереальна фото зона для твого контенту</span
				>
			</div>
			<div>
				<Check /><span
					>Професійний фотограф і доступ до фотографій після конференції</span
				>
			</div>
		</div>
		<div class="content">
			<div><Check /><span>Живий Nail-маркет від топових брендів</span></div>
		</div>
	</div>

	<button>Купити білет</button>
</section>

<style>
	section {
		position: relative;
		width: var(--container-width);
		margin: 0 auto;
	}
	button {
		margin: 50px auto;
		padding: 10px 35px;
		color: var(--text-color);
		display: block;
		font-size: 20px;
		border-radius: 30px;
		background-color: rgba(239, 68, 68, 0.662);
	}
	button:hover {
		background-color: rgba(239, 68, 68);
	}

	section :global(.title) {
		margin-bottom: 50px;
		text-align: center;
	}

	.benefits {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		gap: 10px;
		height: 400px;
		width: 100%;
		border-radius: 35px;
		line-height: 1.5;
	}
	@media (max-width: 768px) {
		.benefits {
			flex-direction: column;
			height: auto;
		}
		.benefits .content {
			border-radius: 35px;
			width: 100%;
		}

		button {
			background-color: rgba(239, 68, 68);
		}
	}

	.benefits .content {
		background-color: var(--color-bg-1);
		flex: 1;
		height: 100%;
	}
	.benefits .content {
		background-color: hsla(0, 0%, 100%, 0.05);
		transition-property:
			background-color,
			backdrop-filter transform;
		transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
		transition-duration: 0.15s;
		backdrop-filter: blur(8px);
		font-size: 20px;
		line-height: 1.5;
		display: flex;
		flex-direction: column;
		gap: 20px;
		justify-content: center;
		align-items: center;
		padding: 20px 10px;
		text-align: start;
		height: 100%;
	}
	.benefits .content:hover {
		background-color: hsla(0, 0%, 100%, 0.1); /* More opaque on hover */
		transform: scale(1.02); /* Scale the element up on hover */
		transition-duration: 0.2s;
	}

	.benefits .content:nth-child(1) {
		border-top-left-radius: 35px;
		border-bottom-left-radius: 35px;
	}
	.benefits .content:nth-child(4) {
		border-top-right-radius: 35px;
		border-bottom-right-radius: 35px;
	}
	.content div {
		display: flex;
		align-items: center;
		gap: 10px;
	}
</style>
