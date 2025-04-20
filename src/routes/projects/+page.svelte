<!-- src/routes/projects/+page.svelte -->
<svelte:head>
	<title>Projects by Edgars Cirulis</title>
</svelte:head>

<section class="section">
	<h1>Projects</h1>
	<div class="divider"></div>

	<div class="projects-grid">
		<article class="project-card">
			<h3>Portfolio Website</h3>
			<p>A performant personal site built with SvelteKit and modern CSS</p>
			<div class="tech-stack">
				<span>SvelteKit</span>
				<span>Vite</span>
				<span>WebGL</span>
			</div>
		</article>

		<article class="project-card">
			<h3>Shader Playground</h3>
			<p>Interactive WebGL shader experimentation environment</p>
			<div class="tech-stack">
				<span>Three.js</span>
				<span>GLSL</span>
				<span>TypeScript</span>
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

	.projects-grid {
		display: grid;
		gap: 2rem;
		grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
		width: 100%;
	}

	.project-card {
		background: var(--card-bg);
		backdrop-filter: blur(10px);
		padding: 1.5rem;
		border-radius: 1rem;
		border: 1px solid var(--card-border);
		transition: transform 0.3s ease;
	}

	.project-card:hover {
		transform: translateY(-5px);
	}

	.project-card h3 {
		font-size: 1.5rem;
		margin-bottom: 1rem;
		color: var(--heading-color);
	}

	.project-card p {
		line-height: 1.7;
		color: var(--text-color);
		margin-bottom: 1rem;
	}

	.tech-stack {
		display: flex;
		gap: 0.8rem;
		flex-wrap: wrap;
		justify-content: center;
	}

	.tech-stack span {
		font-size: 0.9rem;
		background: var(--secondary-bg);
		color: var(--text-color);
		padding: 0.5rem 1.2rem;
		border-radius: 2rem;
	}

	@media (max-width: 768px) {
		.section {
			padding: 3rem 1rem;
		}

		h1 {
			font-size: 2rem;
		}

		.projects-grid {
			gap: 1.5rem;
		}

		.project-card {
			padding: 1.2rem;
		}

		.project-card h3 {
			font-size: 1.3rem;
		}

		.project-card p {
			font-size: 0.9rem;
		}

		.tech-stack span {
			font-size: 0.8rem;
			padding: 0.4rem 1rem;
		}
	}
</style>
