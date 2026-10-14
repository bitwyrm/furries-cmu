<script>
	import { photoSlides } from '#lib/content.js';

	let active = $state(0);
	let current = $derived(photoSlides[active]);

	function move(step) {
		active = (active + step + photoSlides.length) % photoSlides.length;
	}
</script>

<div class="photo-gallery" role="region" aria-label="Club photo slideshow">
	<div class="photo-gallery__topline">
		<span>FIELD NOTES / PHOTO ROLL</span>
		<span>{String(active + 1).padStart(2, '0')} — {String(photoSlides.length).padStart(2, '0')}</span>
	</div>

	<figure class="photo-gallery__figure">
		<div class="photo-stage scene-{current.palette}" role="img" aria-label={current.title}>
			<div class="photo-stage__mat">
				<span class="photo-stage__stamp">{current.tag}</span>
				<span class="photo-stage__big">ADD<br />PHOTO</span>
				<span class="photo-stage__corner photo-stage__corner--one"></span>
				<span class="photo-stage__corner photo-stage__corner--two"></span>
				<span class="photo-stage__note">image slot<br />not developed</span>
			</div>
			<span class="photo-stage__registration" aria-hidden="true">F@C</span>
		</div>
		<figcaption class="photo-gallery__caption">
			<strong>{current.title}</strong>
			<span>{current.caption}</span>
		</figcaption>
	</figure>

	<div class="photo-gallery__controls">
		<div class="photo-gallery__arrows">
			<button type="button" aria-label="Previous photo" onclick={() => move(-1)}>← <span>PREV</span></button>
			<button type="button" aria-label="Next photo" onclick={() => move(1)}><span>NEXT</span> →</button>
		</div>
		<div class="photo-gallery__dots" role="group" aria-label="Choose a photo">
			{#each photoSlides as slide, index}
				<button
					type="button"
					class:active={active === index}
					aria-label="Show {slide.tag.toLowerCase()}"
					aria-pressed={active === index}
					onclick={() => (active = index)}
				></button>
			{/each}
		</div>
	</div>
</div>

<style>
	.photo-gallery {
		width: 100%;
		max-width: 850px;
		margin-inline: auto;
		padding: clamp(14px, 2.2vw, 28px);
		background: var(--sand);
		border: 2px solid var(--ink);
		box-shadow: 9px 10px 0 var(--ink);
		transform: rotate(-0.45deg);
	}

	.photo-gallery__topline,
	.photo-gallery__controls,
	.photo-gallery__arrows {
		display: flex;
		align-items: center;
		justify-content: space-between;
		gap: 14px;
	}

	.photo-gallery__topline {
		margin-bottom: 12px;
		font: 700 0.76rem/1.3 'IBM Plex Mono', monospace;
		letter-spacing: 0.07em;
	}

	.photo-gallery__figure { margin: 0; }

	.photo-stage {
		position: relative;
		display: grid;
		min-height: clamp(280px, 44vw, 500px);
		place-items: center;
		overflow: hidden;
		border: 2px solid var(--ink);
		background-color: var(--tomato);
		background-image: radial-gradient(var(--ink) 0.8px, transparent 0.8px);
		background-size: 9px 9px;
	}

	.scene-blue { background-color: var(--blue); }
	.scene-red { background-color: var(--blood); }
	.scene-clay { background-color: var(--clay); }

	.photo-stage__mat {
		position: relative;
		display: grid;
		width: min(75%, 590px);
		min-height: 70%;
		aspect-ratio: 1.55;
		place-items: center;
		overflow: hidden;
		background: var(--paper);
		border: 2px solid var(--ink);
		box-shadow: 10px 10px 0 var(--ink);
		transform: rotate(1.4deg);
	}

	.photo-stage__mat::before,
	.photo-stage__mat::after {
		position: absolute;
		inset: 0;
		content: '';
		pointer-events: none;
	}

	.photo-stage__mat::before {
		background: repeating-linear-gradient(0deg, transparent 0 5px, rgba(var(--night-rgb), 0.07) 5px 6px);
	}

	.photo-stage__mat::after {
		inset: 10px;
		border: 1px dashed rgba(var(--night-rgb), 0.53);
	}

	.photo-stage__big {
		position: relative;
		z-index: 1;
		color: var(--blood);
		font: 700 clamp(2.1rem, 7vw, 5rem)/0.94 'Silkscreen', monospace;
		text-align: center;
		transform: rotate(-3deg);
	}

	.photo-stage__stamp,
	.photo-stage__note {
		position: absolute;
		z-index: 2;
		font: 700 0.68rem/1.3 'IBM Plex Mono', monospace;
		letter-spacing: 0.08em;
	}

	.photo-stage__stamp { top: 18px; left: 20px; }
	.photo-stage__note { right: 20px; bottom: 18px; text-align: right; }

	.photo-stage__corner {
		position: absolute;
		z-index: 1;
		width: 35px;
		height: 35px;
		background: var(--clay);
		image-rendering: pixelated;
		clip-path: polygon(0 0, 100% 0, 100% 45%, 66% 45%, 66% 66%, 45% 66%, 45% 100%, 0 100%);
	}

	.photo-stage__corner--one { top: 20%; left: 14%; transform: rotate(180deg); }
	.photo-stage__corner--two { right: 15%; bottom: 19%; transform: rotate(0deg); }

	.photo-stage__registration {
		position: absolute;
		right: 12px;
		bottom: 5px;
		color: var(--paper);
		font: 700 1.1rem/1 'Silkscreen', monospace;
		text-shadow: 2px 2px var(--ink);
		transform: rotate(-8deg);
	}

	.photo-gallery__caption {
		display: flex;
		align-items: baseline;
		justify-content: space-between;
		gap: 18px;
		padding-top: 13px;
		font-size: 0.94rem;
	}

	.photo-gallery__caption strong {
		font: 700 1.05rem/1.3 'IBM Plex Mono', monospace;
	}

	.photo-gallery__caption span { max-width: 54%; text-align: right; }

	.photo-gallery__controls { padding-top: 13px; }
	.photo-gallery__arrows { gap: 8px; }

	.photo-gallery button {
		min-height: 42px;
		padding: 6px 11px;
		color: var(--ink);
		background: transparent;
		border: 1px solid var(--ink);
		font: 700 0.82rem/1 'IBM Plex Mono', monospace;
		cursor: pointer;
	}

	.photo-gallery button:hover,
	.photo-gallery button:focus-visible { color: var(--paper); background: var(--ink); }
	.photo-gallery button:focus-visible { outline: 3px solid var(--blue); outline-offset: 3px; }

	.photo-gallery__dots { display: flex; gap: 8px; }
	.photo-gallery__dots button { width: 15px; min-height: 15px; padding: 0; border-radius: 50%; }
	.photo-gallery__dots button.active { background: var(--blood); }

	@media (max-width: 600px) {
		.photo-gallery { padding: 12px; box-shadow: 5px 6px 0 var(--ink); transform: rotate(-0.25deg); }
		.photo-gallery__topline { font-size: 0.66rem; }
		.photo-stage { min-height: 310px; }
		.photo-stage__mat { width: 82%; min-height: 64%; }
		.photo-stage__stamp { top: 12px; left: 13px; font-size: 0.6rem; }
		.photo-stage__note { right: 13px; bottom: 12px; font-size: 0.58rem; }
		.photo-gallery__caption { align-items: flex-start; flex-direction: column; gap: 4px; }
		.photo-gallery__caption span { max-width: none; text-align: left; }
		.photo-gallery__arrows button { padding-inline: 8px; }
	}
</style>
