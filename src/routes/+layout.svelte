<!-- src/routes/+layout.svelte -->
<script>
	const year = new Date().getFullYear();
	let isDarkTheme = true;

	function toggleTheme() {
		isDarkTheme = !isDarkTheme;
		document.documentElement.setAttribute('data-theme', isDarkTheme ? 'dark' : 'light');
	}
</script>

<div class="background-wrapper">
	<div class="gradient-bg"></div>
</div>

<nav class="navbar" aria-label="Main Navigation">
	<div class="nav-inner">
		<a href="/" class="logo">Edgars Cirulis</a>

		<div class="nav-right">
			<button class="theme-toggle" on:click={toggleTheme} aria-label="Toggle Theme">
				{#if isDarkTheme}
					☀️
				{:else}
					🌙
				{/if}
			</button>

			<input id="menu-toggle" type="checkbox" />
			<label class="menu-icon" for="menu-toggle">
				<span class="hamburger"></span>
			</label>

			<div class="links">
				<a href="/">Home</a>
				<a href="/about">About</a>
				<a href="/projects">Projects</a>
				<a href="/hobbies">Hobbies</a>
			</div>
		</div>
	</div>
</nav>

<main>
	<slot />
</main>

<footer class="footer" aria-label="Footer">
	<p>© {year} Edgars Cirulis</p>
	<p>
		<a href="mailto:edgarsciruliss@email.com">Email</a> •
		<a href="https://github.com/Edgars-Cirulis" target="_blank" rel="noopener noreferrer">GitHub</a>
	</p>
</footer>

<style>
	:global(:root) {
		--background: radial-gradient(circle at 50% 50%, #0a0a0a 0%, #000 100%);
		--text-color: #e6e6e6;
		--heading-color: #ffffff;
		--card-bg: rgba(30, 30, 30, 0.5);
		--card-border: rgba(255, 255, 255, 0.15);
		--secondary-bg: rgba(165, 134, 255, 0.15);
		--secondary-border: rgba(165, 134, 255, 0.3);
		--navbar-bg: rgba(10, 10, 10, 0.9);
		--navbar-border: #222;
		--footer-text: #bbbbbb;
		--placeholder-bg: rgba(255, 255, 255, 0.1);
		--accent-primary: #a586ff;
		--accent-secondary: #ff7cf5;
	}

	:global([data-theme='light']) {
		--background: radial-gradient(circle at 50% 50%, #f5f5f5 0%, #e0e0e0 100%);
		--text-color: #333333;
		--heading-color: #1a1a1a;
		--card-bg: rgba(255, 255, 255, 0.5);
		--card-border: rgba(0, 0, 0, 0.1);
		--secondary-bg: rgba(165, 134, 255, 0.15);
		--secondary-border: rgba(165, 134, 255, 0.3);
		--navbar-bg: rgba(255, 255, 255, 0.9);
		--navbar-border: #dddddd;
		--footer-text: #666666;
		--placeholder-bg: rgba(0, 0, 0, 0.1);
		--accent-primary: #a586ff;
		--accent-secondary: #ff7cf5;
	}

	:global(html, body) {
		margin: 0;
		padding: 0;
		font-family: 'Space Grotesk', sans-serif;
		scroll-behavior: smooth;
		background: var(--background);
	}

	.background-wrapper {
		position: fixed;
		inset: 0;
		z-index: -1;
	}

	.gradient-bg {
		position: absolute;
		inset: 0;
		background: linear-gradient(45deg, var(--accent-primary), var(--accent-secondary));
		background-size: 400%;
		animation: gradientShift 20s ease infinite;
	}

	@keyframes gradientShift {
		0% {
			background-position: 0% 50%;
		}
		50% {
			background-position: 100% 50%;
		}
		100% {
			background-position: 0% 50%;
		}
	}

	main {
		position: relative;
		z-index: 1;
	}

	.navbar {
		position: sticky;
		top: 0;
		z-index: 100;
		padding: 1rem 1.5rem;
		background: var(--navbar-bg);
		backdrop-filter: blur(14px);
		border-bottom: 1px solid var(--navbar-border);
	}

	.nav-inner {
		max-width: 1100px;
		margin: 0 auto;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}

	.nav-right {
		display: flex;
		align-items: center;
		gap: 1rem;
	}

	.logo {
		font-weight: 700;
		font-size: 1.3rem;
		color: var(--accent-primary);
		text-decoration: none;
	}

	.theme-toggle {
		background: none;
		border: none;
		font-size: 1.2rem;
		cursor: pointer;
	}

	.menu-icon {
		display: none;
		cursor: pointer;
	}

	.hamburger {
		display: block;
		width: 24px;
		height: 2px;
		background: var(--accent-primary);
		position: relative;
	}

	.hamburger::before,
	.hamburger::after {
		content: '';
		position: absolute;
		width: 24px;
		height: 2px;
		background: var(--accent-primary);
		transition: all 0.3s ease;
	}

	.hamburger::before {
		top: -8px;
	}

	.hamburger::after {
		top: 8px;
	}

	#menu-toggle {
		display: none;
	}

	#menu-toggle:checked ~ .menu-icon .hamburger {
		background: transparent;
	}

	#menu-toggle:checked ~ .menu-icon .hamburger::before {
		transform: rotate(45deg);
		top: 0;
	}

	#menu-toggle:checked ~ .menu-icon .hamburger::after {
		transform: rotate(-45deg);
		top: 0;
	}

	.links {
		display: flex;
		gap: 2rem;
	}

	.links a {
		color: var(--text-color);
		text-decoration: none;
		font-size: 1rem;
		position: relative;
		transition: color 0.3s ease;
	}

	.links a::after {
		content: '';
		position: absolute;
		bottom: -4px;
		left: 0;
		width: 0;
		height: 2px;
		background: var(--accent-primary);
		transition: width 0.3s ease;
	}

	.links a:hover {
		color: var(--accent-secondary);
	}

	.links a:hover::after {
		width: 100%;
	}

	@media (max-width: 768px) {
		.menu-icon {
			display: block;
			z-index: 101;
		}

		.links {
			display: none;
			position: fixed;
			top: 0;
			left: 0;
			width: 100%;
			height: 100vh;
			background: var(--navbar-bg);
			backdrop-filter: blur(14px);
			flex-direction: column;
			align-items: center;
			justify-content: center;
			gap: 2.5rem;
			z-index: 100;
		}

		.links a {
			font-size: 1.5rem;
			color: var(--text-color);
		}

		#menu-toggle:checked ~ .links {
			display: flex;
		}

		#menu-toggle:checked ~ .menu-icon {
			position: fixed;
			top: 1rem;
			right: 1.5rem;
		}
	}

	.footer {
		text-align: center;
		padding: 2rem 1.5rem;
		font-size: 0.9rem;
		color: var(--footer-text);
		background: var(--navbar-bg);
		backdrop-filter: blur(12px);
		border-top: 1px solid var(--navbar-border);
		position: relative;
		z-index: 1;
	}

	.footer p {
		margin: 0.5rem 0;
	}

	.footer a {
		color: var(--accent-primary);
		text-decoration: none;
		margin: 0 0.5rem;
		transition: color 0.3s ease;
	}

	.footer a:hover {
		color: var(--accent-secondary);
	}
</style>
