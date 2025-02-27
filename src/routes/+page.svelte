<script>
	import '../app.css';

	const today = new Date();
	const firstOfMarch = new Date(2025, 2, 1);
	const isSpiegel = today < firstOfMarch;
</script>

<div class="app-container" style:--primary-color={isSpiegel ? '#e64415' : '#007aff'}>
	<div class="underlay">
		<p class="date">{today.toLocaleDateString()}</p>
		<p class="byline">Alles Gute, Martin!</p>
	</div>
	<main>
		<!-- svelte-ignore a11y_img_redundant_alt -->
		<h1>
			Ist <a href="https://de.linkedin.com/in/martin-schön-7a95021a5"
				>Martin<img src="/martin.jpeg" alt="Image of Martin when he still was at Der Spiegel" /></a
			> noch beim Spiegel?
		</h1>
		<p class="answer">{isSpiegel ? 'Ja!' : 'Nein,'}</p>
		{#if !isSpiegel}
			<p class="tagesschau">er ist jetzt bei der Tagesschau!</p>
		{/if}
	</main>
</div>

<style>
	.app-container {
		position: relative;
		z-index: 5;
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

	.underlay {
		position: absolute;
		top: 0;
		right: 0;
		bottom: 0;
		left: 0;
		z-index: 0;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: space-between;
		padding: 2rem 1rem;
	}

	h1 {
		margin: 0;
		padding: 0;
		font-family: 'SpiegelSans4UI', sans-serif;
		font-weight: normal;
		font-size: 2rem;
		text-align: center;
		color: snow;
	}

	h1 a {
		position: relative;
		display: inline-block;
		background: white;
		border: none;
		border-radius: 0.675rem;
		padding: 0.125rem 0.5rem;
		font-weight: bold;
		color: var(--primary-color);
    text-decoration: none;
	}

	h1 a img {
		position: absolute;
		top: -3rem;
		right: -1.5rem;
		width: 40px;
		height: 40px;
		margin: 1rem 0;
		border: 3px solid white;
		border-radius: 50%;
	}

	p {
		margin: 0;
		padding: 0;
		text-align: center;
	}

	p.answer,
	p.tagesschau {
		animation: fadein 2s ease-in;
		color: white;
	}

	p.answer {
		font-family: 'SpiegelSlab4UICd', sans-serif;
		font-size: 6rem;
		line-height: 1.2;
	}

	p.tagesschau {
		font-family: 'SpiegelSans4UI', sans-serif;
		font-size: 1.5rem;
	}

	p.byline,
	p.date {
		font-family: 'SpiegelSans4UI', sans-serif;
		font-size: 1.25rem;
		color: whitesmoke;
		opacity: 0.8;
	}

	@keyframes fadein {
		from {
			opacity: 0;
		}
		to {
			opacity: 1;
		}
	}
</style>
