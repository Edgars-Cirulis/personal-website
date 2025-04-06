<script lang="ts">
	import { onMount } from 'svelte';

	let name = '';
	let contact = '';
	let submitted = false;
	let countdown = '';

	const BIN_ID = '67f176088a456b79668312d7';
	const API_KEY = '$2a$10$LmPnwXyNfEeFpJwif2YQC.66geJxMlKaZeseynh9mJP1TPH8fuo6C';

	const giveawayDeadline = new Date('2025-04-10T00:00:00+03:00');

	onMount(() => {
		if (localStorage.getItem('hasEnteredGiveaway') === 'true') {
			submitted = true;
		}

		updateCountdown();
		const interval = setInterval(updateCountdown, 1000);
		return () => clearInterval(interval);
	});

	function updateCountdown() {
		const now = new Date();
		const diff = giveawayDeadline.getTime() - now.getTime();

		if (diff <= 0) {
			countdown = 'Izloze ir beigusies!';
			return;
		}

		const days = Math.floor(diff / (1000 * 60 * 60 * 24));
		const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
		const minutes = Math.floor((diff / (1000 * 60)) % 60);
		const seconds = Math.floor((diff / 1000) % 60);

		countdown = `${days}d ${hours}h ${minutes}min ${seconds}s`;
	}

	async function handleSubmit(event: SubmitEvent) {
		event.preventDefault();

		if (!name.trim() || !contact.trim()) {
			alert('Lūdzu ievadi savu vārdu un kontaktinformāciju.');
			return;
		}

		const newEntry = {
			vards: name,
			kontakts: contact,
			laiks: new Date().toISOString()
		};

		try {
			const getRes = await fetch(`https://api.jsonbin.io/v3/b/${BIN_ID}/latest`, {
				headers: {
					'X-Master-Key': API_KEY
				}
			});
			const currentData = await getRes.json();
			const entries = currentData.record.entries || [];

			entries.push(newEntry);

			const putRes = await fetch(`https://api.jsonbin.io/v3/b/${BIN_ID}`, {
				method: 'PUT',
				headers: {
					'Content-Type': 'application/json',
					'X-Master-Key': API_KEY
				},
				body: JSON.stringify({ entries })
			});

			if (putRes.ok) {
				localStorage.setItem('hasEnteredGiveaway', 'true');
				submitted = true;
			} else {
				alert('Neizdevās saglabāt datus. Mēģini vēlreiz.');
			}
		} catch (error) {
			console.error(error);
			alert('Radās kļūda savienojoties ar JSONBin.');
		}
	}
</script>

<section class="giveaway">
	{#if !submitted}
		<div class="form-card">
			<h1>🎉 <span>50 Euro Izloze</span></h1>
			<p class="countdown">⏳ Izloze beigsies pēc: {countdown}</p>

			<form on:submit={handleSubmit}>
				<label>
					<span>Vārds</span>
					<input type="text" bind:value={name} placeholder="Tavs vārds" required />
				</label>

				<label>
					<span>E-pasts vai Telefona Nr.</span>
					<input
						type="text"
						bind:value={contact}
						placeholder="tu@example.com vai 20012345"
						required
					/>
				</label>

				<button type="submit">Piedalīties izlozē</button>
			</form>
		</div>
	{:else}
		<p class="thanks">🎉 Paldies par dalību! Lai veicas!</p>
	{/if}
</section>

<div id="about" style="display: none;"></div>
<div id="projects" style="display: none;"></div>

<style>
	.giveaway {
		display: flex;
		align-items: center;
		justify-content: center;
		min-height: 80vh;
		padding: 2rem;
	}

	.form-card {
		background: rgba(255, 255, 255, 0.03);
		padding: 2.5rem 2rem;
		border-radius: 1.5rem;
		box-shadow: 0 0 30px rgba(200, 191, 255, 0.1);
		width: 100%;
		max-width: 480px;
		backdrop-filter: blur(16px);
		text-align: center;
		border: 1px solid #111;
		transition: all 0.3s ease-in-out;
	}

	h1 {
		font-size: 2.2rem;
		background: linear-gradient(90deg, #c8bfff, #e0d4ff);
		background-clip: text;
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		font-weight: 700;
	}

	.countdown {
		color: #c8bfff;
		font-size: 1.2rem;
		margin-bottom: 1.5rem;
		animation: pulse 2s infinite;
	}

	@keyframes pulse {
		0% {
			opacity: 1;
		}
		50% {
			opacity: 0.6;
		}
		100% {
			opacity: 1;
		}
	}

	form {
		display: flex;
		flex-direction: column;
		gap: 1.5rem;
	}

	label {
		display: flex;
		flex-direction: column;
		text-align: left;
		color: #ccc;
		font-size: 0.95rem;
	}

	input {
		margin-top: 0.5rem;
		padding: 0.8rem 1rem;
		background: #111;
		border: none;
		border-radius: 0.75rem;
		color: #eee;
		font-size: 1rem;
		transition: 0.2s ease;
		outline: none;
	}

	input:focus {
		border: 1px solid #c8bfff;
		box-shadow: 0 0 0 2px rgba(200, 191, 255, 0.2);
	}

	button {
		background: #c8bfff;
		color: #000;
		font-weight: 600;
		padding: 0.9rem;
		border: none;
		border-radius: 0.75rem;
		cursor: pointer;
		font-size: 1rem;
		transition: 0.2s ease;
	}

	button:hover {
		transform: scale(1.03);
		background: #d8ccff;
		box-shadow: 0 0 12px rgba(200, 191, 255, 0.2);
	}

	.thanks {
		color: #c8bfff;
		font-size: 1.4rem;
		text-align: center;
		padding: 4rem 2rem;
		max-width: 600px;
		margin: 0 auto;
	}

	@media (max-width: 480px) {
		.giveaway {
			padding: 1rem;
		}

		.form-card {
			width: 100%;
		}

		h1 {
			font-size: 1.8rem;
		}

		.countdown {
			font-size: 1rem;
		}

		input,
		button {
			font-size: 1rem;
		}
	}
</style>
