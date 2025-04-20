<!-- src/routes/+page.svelte -->
<script>
	import { onMount } from 'svelte';

	let taglineText = '';
	const fullTagline = 'Frontend Developer • Creative Coder';

	onMount(() => {
		let i = 0;
		const type = () => {
			if (i < fullTagline.length) {
				taglineText += fullTagline.charAt(i);
				i++;
				setTimeout(type, 100);
			}
		};
		type();
	});
</script>

<svelte:head>
	<title>Edgars Cirulis — Frontend Developer & Creative Coder</title>
	<meta
		name="description"
		content="Edgars Cirulis, a frontend developer and creative coder based in Latvia. Specializing in SvelteKit and building performant web experiences."
	/>
</svelte:head>

<section class="hero">
	<div class="profile-image-wrapper">
		<picture>
			<source srcset="/profile.webp" type="image/webp" />
			<source srcset="/profile.jpg" type="image/jpeg" />
			<img
				src="/profile.jpg"
				alt="Edgars Cirulis"
				class="profile-pic"
				width="160"
				height="160"
				fetchpriority="high"
			/>
		</picture>
	</div>

	<h1>Edgars Cirulis</h1>
	<p class="tagline">{taglineText}<span class="cursor">|</span></p>
	<p class="desc">Building intuitive interfaces by day, exploring creative tech by night.</p>
	<div class="cta-container">
		<a class="button primary" href="/projects">View Work</a>
		<a class="button secondary" href="/about">About Me</a>
	</div>

	<div class="tech-stack">
		<h2>Tech Stack</h2>
		<div class="stack-items">
			<span>SvelteKit</span>
			<span>WebGL</span>
			<span>Vulkan</span>
			<span>Rust</span>
			<span>Three.js</span>
			<span>OpenGL</span>
			<span>SDL2</span>
			<span>C++</span>
		</div>
	</div>
</section>

<style>
	.hero {
		min-height: 80vh;
		padding: 4rem 2rem;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		text-align: center;
	}

	.profile-image-wrapper {
		margin-bottom: 2rem;
		position: relative;
	}

	.profile-pic {
		width: 160px;
		height: 160px;
		border-radius: 50%;
		object-fit: cover;
		border: 3px solid var(--card-border);
		background: radial-gradient(circle, #2b2b2b 0%, #000 100%);
		box-shadow: 0 0 40px rgba(165, 134, 255, 0.2);
		transition:
			transform 0.3s ease,
			box-shadow 0.3s ease;
	}

	.profile-pic:hover {
		transform: scale(1.05);
	}

	.profile-image-wrapper::before {
		content: '';
		position: absolute;
		inset: -20px;
		border-radius: 50%;
		background: radial-gradient(circle, var(--accent-primary) 40, transparent 70%);
		animation: glowPulse 3s ease-in-out infinite;
		z-index: -1;
	}

	@keyframes glowPulse {
		0%,
		100% {
			opacity: 0.3;
			transform: scale(1);
		}
		50% {
			opacity: 0.6;
			transform: scale(1.1);
		}
	}

	h1 {
		font-size: 3rem;
		color: var(--heading-color);
		margin-bottom: 0.5rem;
		line-height: 1.4;
		background: linear-gradient(90deg, var(--accent-primary), var(--accent-secondary));
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
	}

	.tagline {
		color: var(--accent-primary);
		font-size: 1.5rem;
		margin-bottom: 1.5rem;
	}

	.cursor {
		display: inline-block;
		animation: blink 0.8s step-end infinite;
	}

	@keyframes blink {
		50% {
			opacity: 0;
		}
	}

	.desc {
		max-width: 640px;
		margin: 0 auto 2rem;
		color: var(--text-color);
		line-height: 1.7;
		font-size: 1rem;
	}

	.cta-container {
		display: flex;
		gap: 1rem;
		margin-bottom: 3rem;
		flex-wrap: wrap;
		justify-content: center;
	}

	.button {
		padding: 0.8rem 2rem;
		font-weight: 600;
		text-decoration: none;
		border-radius: 999px;
		transition: all 0.3s ease;
	}

	.button.primary {
		background: linear-gradient(90deg, var(--accent-primary), var(--accent-secondary));
		color: #000;
		box-shadow: 0 0 20px rgba(165, 134, 255, 0.5);
	}

	.button.primary:hover {
		transform: translateY(-2px);
		box-shadow: 0 0 30px rgba(165, 134, 255, 0.7);
	}

	.button.secondary {
		background: transparent;
		color: var(--accent-primary);
		border: 2px solid var(--accent-primary);
	}

	.button.secondary:hover {
		transform: translateY(-2px);
		border-color: var(--accent-secondary);
		color: var(--accent-secondary);
	}

	.tech-stack {
		text-align: center;
	}

	.tech-stack h2 {
		font-size: 1.5rem;
		margin-bottom: 1rem;
		color: var(--heading-color);
	}

	.stack-items {
		display: flex;
		gap: 0.8rem;
		flex-wrap: wrap;
		justify-content: center;
	}

	.stack-items span {
		font-size: 0.9rem;
		background: var(--secondary-bg);
		color: var(--text-color);
		padding: 0.5rem 1.2rem;
		border-radius: 2rem;
		border: 1px solid var(--secondary-border);
	}

	@media (max-width: 768px) {
		.hero {
			padding: 3rem 1rem;
			min-height: 70vh;
		}

		h1 {
			font-size: 2rem;
		}

		.tagline {
			font-size: 1.2rem;
		}

		.desc {
			font-size: 0.9rem;
			max-width: 90%;
		}

		.cta-container {
			flex-direction: column;
			gap: 1rem;
			width: 100%;
			max-width: 250px;
		}

		.button {
			width: 100%;
			padding: 0.8rem 1.5rem;
		}

		.stack-items {
			gap: 0.5rem;
		}

		.stack-items span {
			font-size: 0.8rem;
			padding: 0.4rem 1rem;
		}
	}
</style>
