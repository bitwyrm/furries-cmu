<script>
	import ZineDivider from '#lib/components/ZineDivider.svelte';
	import { clubAdvisor, officers, siteContent } from '#lib/content.js';

	const content = siteContent.officers;
</script>

<svelte:head>
	<title>Officers · {siteContent.name}</title>
	<meta name="description" content="Meet the Furries@CMU officers, club advisor, and staff member." />
</svelte:head>

<main class="page page--officers min-h-screen">
	<section class="officers-intro content-width" aria-labelledby="officers-title">
		<div class="page-kicker"><span>03 / PEOPLE INDEX</span><span>THE HUMANS BEHIND THE HOWLS</span></div>
		<div class="officers-intro__layout">
			<div>
				<p class="eyebrow">The club is made of people</p>
				<h1 id="officers-title">Meet the<br /><em>organizers.</em></h1>
			</div>
			<p>{content.intro}</p>
		</div>
	</section>

	<ZineDivider from="var(--color-cream)" to="var(--color-cream)" accent="var(--color-orange)" shape="cut" />

	<section class="officer-list content-width" aria-label="Club officer profiles">
		{#each officers as officer, index}
			<article class="officer-profile officer-profile--{index + 1}" style={`--profile-accent: ${officer.accent}`}>
				<div class="officer-profile__media officer-profile__media--{officer.media.length}">
					{#each officer.media as image, imageIndex}
						<figure class="officer-image officer-image--{imageIndex + 1}">
							<!-- Replace this placeholder with an <img src="" alt="{image.alt}"> when the image is ready. -->
							<div class="officer-image__frame" role="img" aria-label="Placeholder: {image.alt}">
								<span class="officer-image__tag">{image.tag}</span>
								<strong class="officer-image__insert">{image.placeholder}</strong>
								<span class="officer-image__number">0{imageIndex + 1}</span>
							</div>
							<figcaption>{image.label}</figcaption>
						</figure>
					{/each}
				</div>
				<div class="officer-profile__copy">
					<div class="officer-role"><span>PEOPLE / 0{index + 1}</span><span>{officer.role}</span></div>
					<h2>{officer.name}</h2>
					<p class="officer-pronouns">{officer.pronouns}</p>
					<p class="officer-theme">{officer.themeNote}</p>
					<p class="officer-bio">{officer.bio}</p>
				</div>
			</article>
		{/each}
	</section>

	<ZineDivider from="var(--color-cream)" to="var(--color-coral)" accent="var(--color-plum)" shape="wave" />

	<section class="advisor-feature" aria-labelledby="advisor-title">
		<div class="advisor-feature__inner">
			<div class="advisor-feature__masthead">
				<span>OUTSIDE THE OFFICER ROSTER</span>
				<span>CLUB ADVISOR + STAFF MEMBER</span>
			</div>
			<div class="advisor-feature__layout">
				<div class="advisor-feature__copy">
					<p class="advisor-feature__eyebrow">ONE MORE FRIEND OF THE DEN</p>
					<h2 id="advisor-title">Our club<br /><em>advisor.</em></h2>
					<div class="advisor-feature__nameplate">
						<span>STAFF / 01</span>
						<strong>{clubAdvisor.name}</strong>
						<p>{clubAdvisor.pronouns}</p>
					</div>
					<p class="advisor-feature__bio">{clubAdvisor.bio}</p>
				</div>
				<div class="advisor-feature__portraits" aria-label="Advisor photo placeholders">
					{#each clubAdvisor.media as image, imageIndex}
						<figure class="advisor-portrait advisor-portrait--{imageIndex + 1}">
							<!-- Replace this placeholder with an <img src="" alt="{image.alt}"> when the image is ready. -->
							<div class="advisor-portrait__frame" role="img" aria-label="Placeholder: {image.alt}">
								<span class="advisor-portrait__tag">{image.tag}</span>
								<strong>{image.placeholder}</strong>
								<span class="advisor-portrait__number">0{imageIndex + 1}</span>
							</div>
							<figcaption>{image.label}</figcaption>
						</figure>
					{/each}
				</div>
			</div>
		</div>
	</section>
	<ZineDivider from="var(--color-coral)" to="var(--color-plum)" accent="var(--color-gold)" shape="cut" />
</main>
