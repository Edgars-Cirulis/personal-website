<!-- src/routes/hobbies/+page.svelte -->
<svelte:head>
	<title>Hobbies & Interests</title>
</svelte:head>

<section class="section">
	<h1>Creative Pursuits</h1>
	<div class="divider"></div>
	<p class="lead">Balancing code with creative exploration</p>

	<div class="hobby-grid">
		<article class="hobby-card">
			<h3>🖌️ Analog Sketching</h3>
			<p>Traditional pencil & ink drawings focusing on architectural forms</p>
			<div class="gallery">
				<div class="art-placeholder" />
				<div class="art-placeholder" />
			</div>
		</article>

		<article class="hobby-card">
			<h3>🎵 Music Production</h3>
			<p>Creating ambient electronic music with modular synths</p>
			<div class="audio-player">
				<div class="waveform-placeholder" />
			</div>
		</article>
	</div>
</section>

<style>
	.section {
		padding: 4rem 2rem;
		max-width: 1100px;
		margin: 0 auto;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	h1 {
		font-size: 3rem;
		text-align: center;
		margin-bottom: 1rem;
		background: linear-gradient(90deg, var(--accent-primary), var(--accent-secondary));
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
	}

	.divider {
		width: 100px;
		height: 2px;
		background: linear-gradient(90deg, var(--accent-primary), var(--accent-secondary));
		margin: 1rem 0 2rem;
	}

	.lead {
		font-size: 1.2rem;
		line-height: 1.7;
		color: var(--accent-primary);
		text-align: center;
		margin-bottom: 2rem;
	}

	.hobby-grid {
		display: grid;
		gap: 2rem;
		grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
		width: 100%;
	}

	.hobby-card {
		background: var(--card-bg);
		backdrop-filter: blur(10px);
		padding: 1.5rem;
		border-radius: 1rem;
		border: 1px solid var(--card-border);
		transition: transform 0.3s ease;
	}

	.hobby-card:hover {
		transform: translateY(-5px);
	}

	.hobby-card h3 {
		font-size: 1.5rem;
		margin-bottom: 1rem;
		color: var(--heading-color);
	}

	.hobby-card p {
		line-height: 1.7;
		color: var(--text-color);
	}

	.art-placeholder {
		height: 200px;
		background: var(--placeholder-bg);
		border-radius: 0.5rem;
		margin: 1rem 0;
	}

	.waveform-placeholder {
		height: 100px;
		background: var(--placeholder-bg);
		border-radius: 0.5rem;
		margin: 1rem 0;
	}

	@media (max-width: 768px) {
		.section {
			padding: 3rem 1rem;
		}

		h1 {
			font-size: 2rem;
		}

		.lead {
			font-size: 1rem;
		}

		.hobby-grid {
			gap: 1.5rem;
		}

		.hobby-card {
			padding: 1.2rem;
		}

		.hobby-card h3 {
			font-size: 1.3rem;
		}

		.hobby-card p {
			font-size: 0.9rem;
		}

		.art-placeholder {
			height: 150px;
		}

		.waveform-placeholder {
			height: 80px;
		}
	}
</style>
