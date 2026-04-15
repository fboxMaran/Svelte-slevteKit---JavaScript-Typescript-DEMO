<script lang="ts">
	type Modo = 'javascript' | 'typescript';

	const agenda = [
		{ bloque: 'Calentamiento', tema: 'Reactividad en 5 minutos', minutos: 15 },
		{ bloque: 'Demo principal', tema: 'Componentes + estado + eventos', minutos: 30 },
		{ bloque: 'Reto express', tema: 'Mini app colaborativa en equipos', minutos: 20 }
	];

	const snippets: Record<Modo, string> = {
		javascript: `let puntos = 0;
function sumar() {
  puntos += 1;
}`,
		typescript: `let puntos: number = 0;
function sumar(): void {
  puntos += 1;
}`
	};

	let modo = $state<Modo>('typescript');
	let participantesActivos = $state(18);
	let energiaClase = $state(72);
	let aplausos = $state(0);

	const metaParticipantes = 30;
	const participacion = $derived(
		Math.min(100, Math.round((participantesActivos / metaParticipantes) * 100))
	);
	const ambiente = $derived(energiaClase >= 80 ? 'Excelente' : energiaClase >= 60 ? 'Muy bueno' : 'Subiendo');

	function sumarAplauso() {
		aplausos += 1;
		energiaClase = Math.min(100, energiaClase + 2);
	}

	function agregarParticipante() {
		participantesActivos = Math.min(metaParticipantes, participantesActivos + 1);
		energiaClase = Math.min(100, energiaClase + 1);
	}
</script>

<svelte:head>
	<title>Demo SvelteKit para Clase</title>
	<meta
		name="description"
		content="Demo visual e interactiva de Svelte/SvelteKit con JavaScript y TypeScript para clase de programación."
	/>
</svelte:head>

<section class="hero">
	<p class="tag">Clase demo • Svelte + SvelteKit</p>
	<h1>Una clase de Lenguajes de Programación, interactiva, alegre y participativa</h1>
	<p class="lead">
		Interfaz que une a estudiantes y profesor. Rápida, reactividad en tiempo real.
	</p>

	<div class="cta-row">
		<button class="btn primary" onclick={agregarParticipante}>+1 ✋ Manito arriba </button>
		<button class="btn ghost" onclick={sumarAplauso}>+1 👏 Aplauso Subir energía</button>
	</div>
</section>

<section class="grid">
	<article class="panel metricas">
		<h2>Panel en vivo de la clase</h2>
		<div class="metric">
			<span>Participación</span>
			<strong>{participacion}%</strong>
		</div>
		<div class="bar">
			<div class="fill cyan" style="width: {participacion}%"></div>
		</div>

		<div class="metric">
			<span>Energía del grupo</span>
			<strong>{energiaClase}% · {ambiente}</strong>
		</div>
		<div class="bar">
			<div class="fill pink" style="width: {energiaClase}%"></div>
		</div>

		<p class="small">
			{participantesActivos}/{metaParticipantes} estudiantes activos · {aplausos} aplausos acumulados
		</p>
	</article>

	<article class="panel">
		<h2>JavaScript vs TypeScript en segundos</h2>
		<div class="switch">
			<button class:active={modo === 'javascript'} onclick={() => (modo = 'javascript')}>
				JavaScript
			</button>
			<button class:active={modo === 'typescript'} onclick={() => (modo = 'typescript')}>
				TypeScript
			</button>
		</div>
		<pre>{snippets[modo]}</pre>
		<p class="small">
			{modo === 'typescript'
				? 'TypeScript ayuda a detectar errores antes de ejecutar.'
				: 'JavaScript permite arrancar rápido con sintaxis flexible.'}
		</p>
	</article>
</section>

<section class="panel agenda">
	<h2>Estructura de la sesión (65 min)</h2>
	<div class="timeline">
		{#each agenda as item}
			<div class="step">
				<p class="block">{item.bloque}</p>
				<p>{item.tema}</p>
				<span>{item.minutos} min</span>
			</div>
		{/each}
	</div>
</section>

<style>
	.hero {
		display: grid;
		gap: 0.75rem;
		padding: 2rem;
		border-radius: 1.2rem;
		background: linear-gradient(140deg, rgb(15 23 42 / 96%), rgb(29 78 216 / 90%), rgb(217 70 239 / 82%));
		color: #f8fafc;
		box-shadow: 0 20px 60px rgb(15 23 42 / 28%);
	}

	.tag {
		display: inline-flex;
		width: fit-content;
		padding: 0.25rem 0.65rem;
		border-radius: 999px;
		background: rgb(255 255 255 / 14%);
		font-size: 0.85rem;
	}

	h1 {
		margin: 0;
		text-align: left;
		font-size: clamp(1.8rem, 4vw, 3rem);
		font-weight: 800;
		line-height: 1.1;
	}

	.lead {
		margin: 0;
		max-width: 56ch;
		color: rgb(241 245 249 / 92%);
	}

	.cta-row {
		display: flex;
		flex-wrap: wrap;
		gap: 0.65rem;
		margin-top: 0.6rem;
	}

	.btn {
		border: 0;
		padding: 0.65rem 1rem;
		border-radius: 0.75rem;
		font-weight: 700;
		cursor: pointer;
	}

	.btn.primary {
		background: #f8fafc;
		color: #0f172a;
	}

	.btn.ghost {
		background: rgb(255 255 255 / 12%);
		color: #f8fafc;
	}

	.grid {
		margin-top: 1rem;
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
		gap: 1rem;
	}

	.panel {
		background: rgb(255 255 255 / 82%);
		backdrop-filter: blur(4px);
		border-radius: 1rem;
		padding: 1rem;
		box-shadow: 0 10px 30px rgb(15 23 42 / 10%);
	}

	h2 {
		margin-top: 0;
		font-size: 1.05rem;
		font-weight: 700;
	}

	.metric {
		display: flex;
		justify-content: space-between;
		margin-top: 0.75rem;
		font-size: 0.95rem;
	}

	.bar {
		height: 0.65rem;
		background: rgb(148 163 184 / 24%);
		border-radius: 999px;
		overflow: hidden;
	}

	.fill {
		height: 100%;
		transition: width 0.3s ease;
	}

	.fill.cyan {
		background: linear-gradient(90deg, #06b6d4, #2563eb);
	}

	.fill.pink {
		background: linear-gradient(90deg, #f43f5e, #d946ef);
	}

	.switch {
		display: flex;
		gap: 0.4rem;
		margin-bottom: 0.6rem;
	}

	.switch button {
		padding: 0.45rem 0.7rem;
		border-radius: 0.65rem;
		border: 1px solid rgb(148 163 184 / 40%);
		background: transparent;
		cursor: pointer;
		font-weight: 700;
	}

	.switch button.active {
		background: #0f172a;
		color: #f8fafc;
		border-color: #0f172a;
	}

	pre {
		margin: 0;
		border-radius: 0.8rem;
		padding: 0.85rem;
		background: #0f172a;
		color: #f8fafc;
		min-height: 6.5rem;
	}

	.small {
		font-size: 0.88rem;
		opacity: 0.85;
		margin-bottom: 0;
	}

	.agenda {
		margin-top: 1rem;
	}

	.timeline {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
		gap: 0.75rem;
	}

	.step {
		padding: 0.75rem;
		border-radius: 0.8rem;
		background: rgb(15 23 42 / 6%);
		border: 1px solid rgb(148 163 184 / 18%);
	}

	.step p {
		margin: 0;
	}

	.block {
		font-weight: 800;
		color: #0f172a;
	}

	.step span {
		display: inline-flex;
		margin-top: 0.4rem;
		font-size: 0.82rem;
		padding: 0.2rem 0.5rem;
		border-radius: 999px;
		background: rgb(14 165 233 / 14%);
		color: #0c4a6e;
	}
</style>
