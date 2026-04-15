<header>
	<div class="brand">
		<p class="title">SvelteKit Live Demo</p>
		<p class="subtitle">Clase de Lenguajes con el Profe Brayitan · JavaScript + TypeScript · Angélica Cabrera y Marlon Badilla</p>
	</div>

	<div class="header-actions">
		<a class="docs" href="https://svelte.dev/docs/kit">Documentación</a>
		<a
			class="docs"
			href="https://github.com/fboxMaran/Svelte-slevteKit---JavaScript-Typescript-DEMO"
			target="_blank"
			rel="noopener noreferrer"
		>
			Git Repo
		</a>
	</div>
</header>

<style>
	header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: 1rem;
		padding: 0.4rem 0;
	}

	.brand p {
		margin: 0;
	}

	.title {
		font-size: 1.1rem;
		font-weight: 800;
		color: #0f172a;
	}

	.subtitle {
		font-size: 0.85rem;
		color: rgb(15 23 42 / 76%);
	}

	.header-actions {
		display: flex;
		align-items: center;
		gap: 0.5rem;
		flex-shrink: 0;
	}

	.docs {
		display: inline-flex;
		align-items: center;
		padding: 0.45rem 0.8rem;
		border-radius: 0.7rem;
		background: #0f172a;
		color: #f8fafc;
		font-size: 0.85rem;
		font-weight: 700;
		text-decoration: none;
	}

	.docs:hover {
		background: #1e293b;
		text-decoration: none;
	}
</style>
