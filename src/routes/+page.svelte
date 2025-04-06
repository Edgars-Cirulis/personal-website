<script></script>

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
				decoding="async"
			/>
		</picture>
	</div>

	<h1>Edgars Cirulis</h1>
	<p class="tagline">Frontend Developer • Indie Dev</p>
	<p class="desc">
		I build fast, clean, thoughtful software. Minimalist by nature, dreamer at heart.
	</p>
	<div class="button-wrapper">
		<a class="button" href="/giveaway">Izloze / Giveaway</a>
		<a class="button" href="#about">About me</a>
	</div>
</section>

<div class="divider"></div>

<section class="section" id="about">
	<h2>About Me</h2>
	<p>
		Hey, I’m Edgars — a self-taught developer from Latvia with a passion for building beautiful,
		fast, and purposeful software. What started as a hobby became an obsession with crafting
		seamless UX.
	</p>
	<p>
		I specialize in frontend development with <strong>SvelteKit</strong>, and also enjoy low-level
		tech like
		<strong>OpenGL</strong>, <strong>Vulkan</strong>, and <strong>SDL2</strong>.
	</p>
	<p>Beyond code: music, analog sketching, coffee, and chasing that clean minimalist aesthetic.</p>
	<p>I’m open to freelance, collaboration, or side projects that are bold, weird, or meaningful.</p>
</section>

<div class="divider"></div>

<section class="section" id="projects">
	<h2>Projects</h2>
	<div class="projects">
		<div class="project-card">
			<h3>Portfolio Website</h3>
			<p>A sleek personal site built with SvelteKit</p>
			<span class="meta">2025 • SvelteKit • Personal</span>
		</div>
	</div>
</section>

<svelte:head>
	<title>Edgars Cirulis — Frontend Developer & Indie Maker in Latvia</title>
	<meta
		name="description"
		content="Edgars Cirulis, a frontend developer and indie maker based in Latvia. Specializing in SvelteKit and building fast, clean, and purposeful web applications."
	/>
	<meta property="og:title" content="Edgars Cirulis — Frontend Developer & Indie Maker in Latvia" />
	<meta
		property="og:description"
		content="Edgars Cirulis, a self-taught developer from Latvia passionate about clean UI and web experiences using SvelteKit."
	/>
	<meta property="og:type" content="website" />
	<meta property="og:url" content="https://edgarscirulis.lv" />

	<!-- Structured Data for Local SEO -->
	<script type="application/ld+json">
		{
			"@context": "https://schema.org",
			"@type": "Person",
			"name": "Edgars Cirulis",
			"url": "https://edgarscirulis.lv",
			"image": "/profile.jpg",
			"jobTitle": "Frontend Developer & Indie Maker",
			"address": {
				"@type": "LV-1064",
				"addressLocality": "Riga",
				"addressCountry": "Latvia"
			},
			"sameAs": ["https://github.com/edgars-cirulis"]
		}
	</script>

	<!-- Geo Tags -->
	<meta name="geo.position" content="56.894812;24.22567" />
	<meta name="ICBM" content="56.894812, 24.22567" />
	<!-- Latitude and Longitude for Riga -->
	<meta name="geo.placename" content="Riga, Latvia" />
	<meta name="geo.region" content="LV" />
</svelte:head>

<style>
	h1 {
		font-size: 3.5rem;
		color: #e6dcff;
		margin-bottom: 0.5rem;
	}

	h2 {
		color: #e6dcff;
		margin-bottom: 1.5rem;
		font-size: 2rem;
	}

	.hero {
		min-height: 100vh;
		padding: 6rem 2rem 4rem;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: flex-start;
		text-align: center;
		position: relative;
		z-index: 1;
		box-sizing: border-box;
	}

	.profile-image-wrapper {
		display: flex;
		justify-content: center;
		align-items: center;
		margin-bottom: 1.5rem;
	}

	.profile-pic {
		width: 180px;
		height: 180px;
		border-radius: 50%;
		object-fit: cover;
		border: 3px solid rgba(255, 255, 255, 0.05);
		background: radial-gradient(circle, #2b2b2b 0%, #000 100%);
		box-shadow:
			0 0 40px rgba(168, 134, 255, 0.2),
			0 0 8px rgba(255, 255, 255, 0.05);
		transition:
			transform 0.3s ease,
			box-shadow 0.3s ease;
		will-change: transform;
	}

	.profile-pic:hover {
		transform: scale(1.05);
		box-shadow: 0 0 50px rgba(168, 134, 255, 0.3);
	}

	.tagline {
		color: #c8bfff;
		font-weight: 500;
		margin-bottom: 1rem;
		font-size: 1.2rem;
	}

	.desc {
		max-width: 640px;
		margin: 0 auto 2rem;
		color: #aaa;
		line-height: 1.6;
	}

	.button-wrapper {
		display: flex;
		gap: 1rem;
	}

	.button {
		background: #a586ff;
		color: black;
		border-radius: 999px;
		padding: 0.8rem 1.8rem;
		font-weight: 600;
		text-decoration: none;
		box-shadow: 0 0 20px #a586ff55;
		transition: all 0.3s ease;
	}

	.button:hover {
		background: #be9aff;
		box-shadow: 0 0 30px #be9affaa;
		transform: scale(1.05);
	}

	.section {
		padding: 5rem 2rem;
		text-align: center;
		max-width: 880px;
		margin: 0 auto;
		position: relative;
		z-index: 1;
		scroll-margin-top: 100px;
	}

	.divider {
		width: 100%;
		height: 1px;
		background: linear-gradient(to right, transparent, #222, transparent);
		margin: 4rem auto;
		max-width: 800px;
	}

	.projects {
		display: flex;
		flex-wrap: wrap;
		justify-content: center;
		gap: 2rem;
		margin-top: 2rem;
	}

	.project-card {
		width: 280px;
		padding: 1.5rem;
		text-align: left;
		border-radius: 1rem;
		background: rgba(255, 255, 255, 0.04);
		border: 1px solid rgba(255, 255, 255, 0.1);
		backdrop-filter: blur(10px);
		transition:
			transform 0.3s,
			box-shadow 0.3s;
	}

	.project-card:hover {
		transform: translateY(-6px);
		box-shadow: 0 0 20px #b58dff33;
	}

	.project-card h3 {
		color: #d1c2ff;
		margin-bottom: 0.5rem;
	}

	.project-card p {
		color: #aaa;
		font-size: 0.95rem;
		line-height: 1.5;
	}

	.meta {
		display: block;
		margin-top: 1rem;
		color: #777;
		font-size: 0.8rem;
	}
</style>
