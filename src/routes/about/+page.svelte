<!-- src/routes/about/+page.svelte -->
<svelte:head>
	<title>About Edgars Cirulis</title>
</svelte:head>

<section class="section">
	<h1>About Me</h1>
	<div class="divider"></div>

	<div class="bio-grid">
		<div class="bio-text">
			<p class="lead">
				Self-taught developer from Riga, Latvia 🇱🇻<br />
				Specializing in performant web experiences and creative coding
			</p>

			<div class="skills">
				<h2>Core Stack</h2>
				<div class="skill-chips">
					<span>SvelteKit</span>
					<span>TypeScript</span>
					<span>Rust</span>
					<span>WebGL</span>
					<span>Vulkan</span>
				</div>
			</div>

			<h2>Philosophy</h2>
			<p>
				I believe in <strong>purposeful minimalism</strong> - stripping away the unnecessary while maintaining
				depth and functionality. Every pixel and byte should serve a clear purpose.
			</p>
		</div>

		<div class="bio-image">
			<div class="map-placeholder" />
			<small>Based in Riga, working globally</small>
		</div>
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

	h2 {
		font-size: 1.5rem;
		margin: 1.5rem 0 1rem;
		color: var(--heading-color);
	}

	.lead {
		font-size: 1.2rem;
		line-height: 1.7;
		color: var(--accent-primary);
		margin-bottom: 1.5rem;
	}

	.bio-grid {
		display: grid;
		gap: 2rem;
		grid-template-columns: 1fr 300px;
		width: 100%;
	}

	.bio-text p {
		line-height: 1.7;
		color: var(--text-color);
	}

	.skill-chips {
		display: flex;
		gap: 0.8rem;
		flex-wrap: wrap;
		margin: 1rem 0 1.5rem;
	}

	.skill-chips span {
		background: var(--secondary-bg);
		color: var(--text-color);
		padding: 0.5rem 1.2rem;
		border-radius: 2rem;
		border: 1px solid var(--secondary-border);
		font-size: 0.9rem;
	}

	.bio-image {
		position: relative;
		background: var(--card-bg);
		backdrop-filter: blur(10px);
		border-radius: 1rem;
		padding: 1rem;
		border: 1px solid var(--card-border);
	}

	.map-placeholder {
		height: 300px;
		background: var(--placeholder-bg);
		border-radius: 0.5rem;
	}

	.bio-image small {
		display: block;
		text-align: center;
		margin-top: 1rem;
		color: var(--footer-text);
	}

	@media (max-width: 768px) {
		.section {
			padding: 3rem 1rem;
		}

		h1 {
			font-size: 2rem;
		}

		h2 {
			font-size: 1.3rem;
		}

		.lead {
			font-size: 1rem;
		}

		.bio-grid {
			grid-template-columns: 1fr;
			gap: 1.5rem;
		}

		.bio-text p {
			font-size: 0.9rem;
		}

		.skill-chips span {
			font-size: 0.8rem;
			padding: 0.4rem 1rem;
		}

		.map-placeholder {
			height: 200px;
		}
	}
</style>
