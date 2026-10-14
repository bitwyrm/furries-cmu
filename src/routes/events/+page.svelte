<script>
	import ZineDivider from '#lib/components/ZineDivider.svelte';
	import { clubActivities, discordInviteUrl, siteContent } from '#lib/content.js';

	const content = siteContent.events;
</script>

<svelte:head>
	<title>Events · {siteContent.name}</title>
	<meta name="description" content="Study groups, fursuit-making, and monthly Howling at the Moon gatherings with Furries@CMU." />
</svelte:head>

<main class="page page--events min-h-screen">
	<section class="event-programs content-width" aria-labelledby="event-programs-title">
		<div class="event-programs__heading">
			<p class="eyebrow">What we do / 01</p>
			<h1 id="event-programs-title">{content.activitiesTitle}</h1>
			<p>{content.activitiesIntro}</p>
		</div>
		<div class="event-programs__list">
			{#each clubActivities as activity, index}
				<article class="event-program event-program--{index + 1}">
					<span class="event-program__mark" aria-hidden="true">{activity.mark}</span>
					<div>
						<h2>{activity.title}</h2>
						{#if activity.subtitle}<p class="event-program__subtitle">{activity.subtitle}</p>{/if}
						<p class="event-program__copy">{activity.copy}</p>
					</div>
				</article>
			{/each}
		</div>
	</section>

	<ZineDivider from="var(--color-cream)" to="var(--color-electric-blue)" accent="var(--color-raspberry)" shape="wave" />

	<section class="moon-bleed" aria-labelledby="events-title">
		<div class="moon-field">
			<div class="moon-poster content-width">
				<div class="moon-copy">
					<p class="eyebrow eyebrow--light">Our recurring ritual / monthly after dark</p>
					<h1 id="events-title">Howling<br /><span>at the</span><br />Moon</h1>
					<p class="moon-copy__intro">{content.copy}</p>
					<ol class="moon-route">
						{#each content.steps as step, index}
							<li><span>{String(index + 1).padStart(2, '0')}</span><strong>{step}</strong></li>
						{/each}
					</ol>
				</div>

				<figure class="moon-art">
					<svg viewBox="0 0 480 420" role="img" aria-labelledby="moon-svg-title moon-svg-desc">
						<title id="moon-svg-title">Pixel moon over a hill</title>
						<desc id="moon-svg-desc">A blocky cream moon and pixel stars sit over a simple red-orange landscape.</desc>
						<rect width="480" height="420" fill="var(--color-electric-blue)" />
						<g fill="var(--color-cream)">
							<rect x="70" y="42" width="12" height="12" /><rect x="118" y="79" width="8" height="8" /><rect x="370" y="43" width="11" height="11" />
							<rect x="418" y="107" width="8" height="8" /><rect x="51" y="164" width="9" height="9" /><rect x="399" y="202" width="12" height="12" />
							<rect x="320" y="90" width="8" height="8" /><rect x="159" y="48" width="7" height="7" />
						</g>
						<path d="M237 50h40v18h26v21h19v27h17v41h-17v25h-20v20h-27v18h-43v-18h-28v-20h-18v-25h-18v-40h18v-29h20V87h29z" fill="var(--color-cream)" />
						<g fill="var(--color-gold)"><rect x="259" y="95" width="14" height="14" /><rect x="300" y="132" width="10" height="10" /><rect x="225" y="150" width="12" height="12" /><rect x="270" y="174" width="9" height="9" /></g>
						<path d="M0 296h75l24-21h52l22 17h63l20-30h43l32 23h66l25-21h58v156H0z" fill="var(--color-raspberry)" />
						<path d="M0 348h92l19-17h64l21 20h46l27-17h60l21 16h49l20-19h61v89H0z" fill="var(--color-coral)" />
					<g fill="var(--color-indigo)"><rect x="82" y="312" width="12" height="12" /><rect x="375" y="300" width="12" height="12" /><rect x="220" y="360" width="9" height="9" /><rect x="28" y="376" width="14" height="14" /></g>
				</svg>
					<div class="date-slip">
						<span class="date-slip__asterisk">✳</span>
						<p class="date-slip__label">Next gathering</p>
						<strong>Check Discord<br />for the date</strong>
						<a href={discordInviteUrl} target="_blank" rel="noopener noreferrer">Find the club ↗</a>
					</div>
					<figcaption>the moon is real / the art is not a schedule</figcaption>
				</figure>
			</div>
		</div>
	</section>

</main>
