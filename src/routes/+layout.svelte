<script>
	const year = new Date().getFullYear();
</script>

<nav class="navbar" aria-label="Main Navigation">
	<div class="nav-inner">
		<span class="logo">Edgars Cirulis</span>

		<input id="menu-toggle" type="checkbox" />
		<label class="menu-icon" for="menu-toggle">&#9776;</label>

		<div class="links">
			<a href="#about">About</a>
			<a href="#stack">Stack</a>
			<a href="#projects">Projects</a>
			<a href="#contact">Contact</a>
		</div>
	</div>
</nav>

<div class="blobs" aria-hidden="true">
	<div class="blob purple"></div>
	<div class="blob pink"></div>
</div>

<main>
	<slot />
</main>

<footer class="footer" id="contact" aria-label="Footer">
	<p>© {year} Edgars Cirulis</p>
	<p>
		<a href="mailto:edgarsciruliss@email.com">Email</a> •
		<a href="https://github.com/Edgars-Cirulis" target="_blank" rel="noopener noreferrer">GitHub</a>
	</p>
</footer>

<style>
	:global(html, body) {
		margin: 0;
		padding: 0;
		font-family: 'Space Grotesk', sans-serif;
		background: #000;
		color: #ddd;
		scroll-behavior: smooth;
		user-select: none;
		-webkit-user-select: none;
	}

	main {
		position: relative;
		z-index: 1;
	}

	.navbar {
		position: sticky;
		top: 0;
		z-index: 100;
		padding: 1rem 2rem;
		background: rgba(0, 0, 0, 0.6);
		backdrop-filter: blur(14px);
		border-bottom: 1px solid #111;
	}

	.nav-inner {
		max-width: 1100px;
		margin: 0 auto;
		display: flex;
		align-items: center;
		justify-content: space-between;
		flex-wrap: wrap;
	}

	.logo {
		font-weight: 700;
		font-size: 1.2rem;
		color: #c8bfff;
	}

	.menu-icon {
		display: none;
		font-size: 1.5rem;
		cursor: pointer;
		color: #c8bfff;
	}

	#menu-toggle {
		display: none;
	}

	.links {
		display: flex;
		gap: 1.5rem;
	}

	.links a {
		color: #aaa;
		text-decoration: none;
		transition: color 0.2s;
	}

	.links a:hover {
		color: #c8bfff;
	}

	@media (max-width: 768px) {
		.menu-icon {
			display: block;
		}

		.links {
			display: none;
			flex-direction: column;
			width: 100%;
			margin-top: 1rem;
		}

		#menu-toggle:checked + .menu-icon + .links {
			display: flex;
		}
	}

	.blobs {
		position: fixed;
		inset: 0;
		z-index: 0;
		pointer-events: none;
		overflow: hidden;
	}

	.blob {
		position: absolute;
		width: 400px;
		height: 400px;
		border-radius: 50%;
		filter: blur(80px);
		opacity: 0.08;
		animation: blobFloat 18s infinite alternate ease-in-out;
	}

	.blob.purple {
		background: #b191ff;
		top: 20%;
		left: -150px;
	}

	.blob.pink {
		background: #ff7cf5;
		bottom: 10%;
		right: -100px;
		animation-delay: 4s;
	}

	@keyframes blobFloat {
		from {
			transform: translate(0, 0);
		}
		to {
			transform: translate(60px, -40px) scale(1.05);
		}
	}

	.footer {
		text-align: center;
		padding: 4rem 2rem;
		font-size: 0.9rem;
		color: #bbb;
		background: rgba(0, 0, 0, 0.6);
		backdrop-filter: blur(12px);
		border-top: 1px solid #111;
	}

	.footer a {
		color: #c8bfff;
		text-decoration: none;
		margin: 0 0.5rem;
	}
</style>
