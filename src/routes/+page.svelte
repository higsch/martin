<script>
	import '../app.css';

	const today = new Date();
	const firstOfMarch = new Date(2025, 2, 1);
	const isSpiegel = today < firstOfMarch;
</script>

<div class="app-container" style:--primary-color={isSpiegel ? '#e64415' : '#007aff'}>
	<main>
		<h1>Ist Martin noch beim Spiegel?</h1>
		<p class="answer">{isSpiegel ? 'Ja!' : 'Nein,'}</p>
		{#if !isSpiegel}
			<p class="tagesschau">er ist jetzt bei der Tagesschau!</p>
		{/if}
	</main>
	<div class="overlay">
		<p class="date">{today.toLocaleDateString()}</p>
		<p class="byline">Alles Gute, Martin!</p>
	</div>
</div>

<style>
	.app-container {
		position: relative;
		z-index: 0;
		width: 100svw;
		height: 100svh;
		background: linear-gradient(white -300%, var(--primary-color) 100%);
	}

	main {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		width: calc(100% - 2rem);
		height: calc(100% - 2rem);
		padding: 1rem;
	}

	.overlay {
		position: absolute;
		top: 0;
		right: 0;
		bottom: 0;
		left: 0;
		z-index: 5;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: space-between;
		padding: 2rem 1rem;
	}

	h1 {
		margin: 0;
		padding: 0;
		font-family: 'SpiegelSans4UI', serif;
		font-weight: normal;
		font-size: 2rem;
		text-align: center;
		color: snow;
	}

	p {
		margin: 0;
		padding: 0;
		text-align: center;
	}

	p.answer {
		font-family: 'SpiegelSlab4UICd', serif;
		font-size: 6rem;
		line-height: 1.2;
		color: white;
	}

	p.tagesschau {
		font-family: 'SpiegelSans4UI', serif;
		font-size: 1.5rem;
		color: white;
	}

	p.byline,
	p.date {
		font-family: 'SpiegelSans4UI', serif;
		font-size: 1.25rem;
		color: whitesmoke;
		opacity: 0.8;
	}
</style>
