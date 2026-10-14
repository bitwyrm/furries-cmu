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
		<div class="photo-stage scene-{current.palette} slide-{active}" role="img" aria-label={current.title}>
			<div class="photo-stage__mat">
				<!-- Uncomment and fill in for a real photo; remove the placeholder labels below:
				<img class="photo-stage__image" src="" alt="" />
				-->
				<span class="photo-stage__stamp">{current.tag}</span>
				<span class="photo-stage__big">ADD<br />PHOTO</span>
				<span class="photo-stage__corner photo-stage__corner--one"></span>
				<span class="photo-stage__corner photo-stage__corner--two"></span>
				<span class="photo-stage__note">image slot<br />not developed</span>
			</div>
			<span class="photo-stage__registration" aria-hidden="true">✳</span>
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
		color: var(--color-plum);
		background: var(--color-gold);
		border: 2px solid var(--color-plum);
		box-shadow: 9px 10px 0 var(--color-plum);
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
		color: var(--color-plum);
		font: 700 0.76rem/1.3 var(--font-mono);
		letter-spacing: 0.07em;
	}

	.photo-gallery__figure { margin: 0; }

	.photo-stage {
		position: relative;
		display: grid;
		min-height: clamp(450px, 43vw, 520px);
		place-items: center;
		overflow: hidden;
		border: 2px solid var(--color-plum);
		background-color: var(--color-coral);
		background-image: radial-gradient(var(--color-plum) 0.8px, transparent 0.8px);
		background-size: 9px 9px;
	}

	.scene-blue { background-color: var(--color-electric-blue); }
	.scene-red { background-color: var(--color-raspberry); }
	.scene-clay { background-color: var(--color-orange); }

	.photo-stage__mat {
		position: relative;
		display: grid;
		width: min(84%, 660px);
		min-height: 76%;
		aspect-ratio: 1.65;
		place-items: center;
		overflow: hidden;
		background: var(--color-cream);
		border: 2px solid var(--color-plum);
		box-shadow: 10px 10px 0 var(--color-plum);
	}

	.slide-0 .photo-stage__mat { transform: rotate(-1.4deg); }
	.slide-1 .photo-stage__mat { transform: rotate(1.25deg); }
	.slide-2 .photo-stage__mat { transform: rotate(-0.7deg); }

	.photo-stage__image {
		position: absolute;
		inset: 0;
		z-index: 0;
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.photo-stage__mat::before,
	.photo-stage__mat::after {
		position: absolute;
		inset: 0;
		content: '';
		pointer-events: none;
	}

	.photo-stage__mat::before {
		background: repeating-linear-gradient(0deg, transparent 0 5px, rgba(var(--rgb-indigo), 0.07) 5px 6px);
	}

	.photo-stage__mat::after {
		inset: 10px;
		border: 1px dashed rgba(var(--rgb-indigo), 0.53);
	}

	.photo-stage__big {
		position: relative;
		z-index: 1;
		color: var(--color-raspberry);
		font: 700 clamp(2.1rem, 7vw, 5rem)/0.94 var(--font-pixel);
		text-align: center;
		transform: rotate(-3deg);
	}

	.photo-stage__stamp,
	.photo-stage__note {
		position: absolute;
		z-index: 2;
		font: 700 0.68rem/1.3 var(--font-mono);
		letter-spacing: 0.08em;
	}

	.photo-stage__stamp { top: 18px; left: 20px; }
	.photo-stage__note { right: 20px; bottom: 18px; text-align: right; }

	.photo-stage__corner {
		position: absolute;
		z-index: 1;
		width: 35px;
		height: 35px;
		background: var(--color-orange);
		image-rendering: pixelated;
		clip-path: polygon(0 0, 100% 0, 100% 45%, 66% 45%, 66% 66%, 45% 66%, 45% 100%, 0 100%);
	}

	.photo-stage__corner--one { top: 20%; left: 14%; transform: rotate(180deg); }
	.photo-stage__corner--two { right: 15%; bottom: 19%; transform: rotate(0deg); }

	.photo-stage__registration {
		position: absolute;
		display: grid;
		width: 31px;
		height: 31px;
		place-items: center;
		right: 12px;
		bottom: 5px;
		color: var(--color-plum);
		background: var(--color-cream);
		border: 1px solid var(--color-plum);
		font: 700 1.1rem/1 var(--font-pixel);
		transform: rotate(-8deg);
	}

	.photo-gallery__caption {
		display: flex;
		align-items: baseline;
		justify-content: space-between;
		gap: 18px;
		padding-top: 13px;
		color: var(--color-plum);
		font-size: 0.94rem;
	}

	.photo-gallery__caption strong {
		font: 700 1.05rem/1.3 var(--font-mono);
	}

	.photo-gallery__caption span { max-width: 54%; text-align: right; }

	.photo-gallery__controls { padding-top: 13px; }
	.photo-gallery__arrows { gap: 8px; }

	.photo-gallery button {
		min-height: 42px;
		padding: 6px 11px;
		color: var(--color-plum);
		background: transparent;
		border: 1px solid var(--color-plum);
		font: 700 0.82rem/1 var(--font-mono);
		cursor: pointer;
	}

	.photo-gallery button:hover,
	.photo-gallery button:focus-visible { color: var(--color-cream); background: var(--color-plum); }
	.photo-gallery button:focus-visible { outline: 3px solid var(--color-electric-blue); outline-offset: 3px; }

	.photo-gallery__dots { display: flex; gap: 8px; }
	.photo-gallery__dots button { width: 15px; min-height: 15px; padding: 0; border-radius: 50%; }
	.photo-gallery__dots button.active { background: var(--color-raspberry); }

	@media (max-width: 640px) {
		.photo-gallery { padding: 12px; box-shadow: 5px 6px 0 var(--color-plum); transform: none; }
		.photo-gallery__topline { font-size: 0.66rem; }
		.photo-stage { min-height: 310px; }
		.photo-stage__mat { width: 88%; min-height: 70%; aspect-ratio: 1.45; }
		.photo-stage__stamp { top: 12px; left: 13px; font-size: 0.6rem; }
		.photo-stage__note { right: 13px; bottom: 12px; font-size: 0.58rem; }
		.photo-gallery__caption { align-items: flex-start; flex-direction: column; gap: 4px; }
		.photo-gallery__caption span { max-width: none; text-align: left; }
		.photo-gallery__arrows button { padding-inline: 8px; }
	}

	@media (min-width: 641px) and (max-width: 900px) {
		.photo-stage { min-height: clamp(350px, 52vw, 460px); }
	}
</style>
